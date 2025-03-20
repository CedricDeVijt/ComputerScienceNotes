# RESTful API Improvements

I'll improve your API to better adhere to RESTful best practices. Here are the key changes:

## 1. Adding Proper API Versioning

```python
# app/main.py (modified part)
# Include API router with version prefix
app.include_router(api_router, prefix="/api/v1")
```

## 2. Restructuring Movie Router with Better Resource Naming

```python
from fastapi import APIRouter, Depends, Path, Query, status
from typing import Optional, List

from app.schemas import ErrorResponse, MovieDetails, MovieList, SimilarMoviesResponse
from app.services.TMDB import (
    TMDBClient, fetch_movie_details_by_id, fetch_popular_movies,
    fetch_similar_genre, fetch_similar_runtime, get_tmdb_client
)
from app.services.quickchart import (
    generate_movie_ratings_chart, generate_movie_ratings_comparison
)

router = APIRouter(prefix="/movies")

@router.get(
    "",
    response_model=MovieList,
    status_code=status.HTTP_200_OK,
    responses={
        status.HTTP_503_SERVICE_UNAVAILABLE: {"model": ErrorResponse},
        status.HTTP_504_GATEWAY_TIMEOUT: {"model": ErrorResponse},
    }
)
async def list_movies(
    page: int = Query(1, ge=1, description="Page number"),
    limit: int = Query(10, ge=1, le=50, description="Results per page"),
    sort_by: str = Query("popularity.desc", description="Sort order"),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    List movies with pagination and sorting.
    """
    result = await fetch_popular_movies(client)
    return {
        "results": result.get("results", []),
        "total_results": result.get("total_results", 0),
        "_links": {
            "self": f"/api/v1/movies?page={page}&limit={limit}&sort_by={sort_by}",
            "next": f"/api/v1/movies?page={page+1}&limit={limit}&sort_by={sort_by}" if page * limit < result.get("total_results", 0) else None
        }
    }

@router.get(
    "/popular",
    response_model=MovieList,
    status_code=status.HTTP_200_OK,
)
async def list_popular_movies(
    page: int = Query(1, ge=1, description="Page number"),
    limit: int = Query(10, ge=1, le=20, description="Results per page"),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    List popular movies with pagination.
    """
    result = await fetch_popular_movies(client)
    return {
        "results": result.get("results", []),
        "total_results": result.get("total_results", 0),
        "_links": {
            "self": f"/api/v1/movies/popular?page={page}&limit={limit}",
            "next": f"/api/v1/movies/popular?page={page+1}&limit={limit}" if page * limit < result.get("total_results", 0) else None
        }
    }

@router.get(
    "/{movie_id}",
    response_model=MovieDetails,
    status_code=status.HTTP_200_OK,
)
async def get_movie(
    movie_id: str = Path(..., description="Movie ID"),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    Get detailed information for a specific movie.
    """
    movie = await fetch_movie_details_by_id(movie_id, client)
    # Add HATEOAS links
    movie["_links"] = {
        "self": f"/api/v1/movies/{movie_id}",
        "similar": f"/api/v1/movies/{movie_id}/similar-movies",
        "favorite": f"/api/v1/favorites/{movie_id}"
    }
    return movie
```

## 3. Creating a Charts Router

```python
# app/routers/charts.py
from fastapi import APIRouter, Depends, Query, status
from typing import List

from app.schemas import ChartResponse, ErrorResponse
from app.services.TMDB import TMDBClient, get_tmdb_client
from app.services.quickchart import generate_movie_ratings_chart

router = APIRouter(prefix="/charts")

@router.get(
    "/movies/ratings",
    response_model=ChartResponse,
    status_code=status.HTTP_200_OK,
    responses={
        status.HTTP_422_UNPROCESSABLE_ENTITY: {"model": ErrorResponse},
        status.HTTP_404_NOT_FOUND: {"model": ErrorResponse},
    }
)
async def create_movie_ratings_chart(
    movie_ids: List[int] = Query(..., description="List of movie IDs", min_items=1),
    width: int = Query(500, ge=200, le=1200),
    height: int = Query(300, ge=200, le=800),
    title: Optional[str] = Query(None),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    Create a chart comparing movie ratings.
    """
    chart_url = await generate_movie_ratings_chart(
        movie_ids=movie_ids,
        width=width,
        height=height,
        title=title or "Movie Ratings Comparison",
        client=client,
    )
    
    return {
        "chart_url": chart_url,
        "_links": {
            "self": f"/api/v1/charts/movies/ratings?movie_ids={','.join(map(str, movie_ids))}"
        }
    }
```

## 4. Improving Comparisons as a Resource

```python
# app/routers/comparisons.py
from fastapi import APIRouter, Depends, Query, status
from typing import List

from app.schemas import MovieRatingsComparison, ErrorResponse
from app.services.TMDB import TMDBClient, get_tmdb_client
from app.services.quickchart import generate_movie_ratings_comparison

router = APIRouter(prefix="/comparisons")

@router.get(
    "/movies",
    response_model=MovieRatingsComparison,
    status_code=status.HTTP_200_OK,
)
async def compare_movies(
    movie_ids: List[int] = Query(..., description="List of movie IDs", min_items=2),
    include_chart: bool = Query(True),
    width: int = Query(500, ge=200, le=1200),
    height: int = Query(300, ge=200, le=800),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    Compare multiple movies by ratings and other metrics.
    """
    comparison = await generate_movie_ratings_comparison(
        movie_ids=movie_ids,
        include_chart=include_chart,
        chart_width=width,
        chart_height=height,
        client=client,
    )
    
    # Add HATEOAS links
    comparison["_links"] = {
        "self": f"/api/v1/comparisons/movies?movie_ids={','.join(map(str, movie_ids))}"
    }
    
    return comparison
```

## 5. Update Similar Movies Resource

```python
# Updated similar movies endpoint in movies.py
@router.get(
    "/{movie_id}/similar-movies",
    response_model=SimilarMoviesResponse,
    status_code=status.HTTP_200_OK,
)
async def list_similar_movies(
    movie_id: str = Path(..., description="Reference movie ID"),
    criteria: str = Query(
        "all", 
        enum=["all", "genre", "runtime"],
    ),
    client: TMDBClient = Depends(get_tmdb_client),
):
    """
    List movies similar to the specified movie.
    """
    # Implementation as before with added HATEOAS links
    response = await get_similar_movies_implementation(movie_id, criteria, client)
    
    # Add HATEOAS links
    response["_links"] = {
        "self": f"/api/v1/movies/{movie_id}/similar-movies?criteria={criteria}",
        "movie": f"/api/v1/movies/{movie_id}"
    }
    
    return response
```

## 6. Update Favorites Router

```python
# app/routers/favorites.py
from fastapi import APIRouter, Depends, Path, status

from app.schemas import FavoriteList, FavoriteResponse
from app.services.TMDB import favorite_movie, fetch_favorites, get_tmdb_client

router = APIRouter(prefix="/favorites")

@router.get(
    "",
    response_model=FavoriteList,
    status_code=status.HTTP_200_OK,
)
async def list_favorites(client = Depends(get_tmdb_client)):
    """
    List favorite movies.
    """
    result = await fetch_favorites(client)
    
    # Add HATEOAS links
    result["_links"] = {
        "self": "/api/v1/favorites"
    }
    
    return result

@router.put(
    "/{movie_id}",
    response_model=FavoriteResponse,
    status_code=status.HTTP_200_OK,
)
async def add_favorite(
    movie_id: int = Path(...),
    client = Depends(get_tmdb_client),
):
    """
    Add a movie to favorites.
    """
    result = await favorite_movie(movie_id, True, client)
    
    # Add HATEOAS links
    result["_links"] = {
        "self": f"/api/v1/favorites/{movie_id}",
        "movie": f"/api/v1/movies/{movie_id}"
    }
    
    return result

@router.delete(
    "/{movie_id}",
    response_model=FavoriteResponse,
    status_code=status.HTTP_200_OK,
)
async def remove_favorite(
    movie_id: int = Path(...),
    client = Depends(get_tmdb_client),
):
    """
    Remove a movie from favorites.
    """
    result = await favorite_movie(movie_id, False, client)
    
    # Add HATEOAS links
    result["_links"] = {
        "self": f"/api/v1/favorites/{movie_id}",
        "movie": f"/api/v1/movies/{movie_id}"
    }
    
    return result
```

## 7. Update Main.py

```python
# app/main.py (additional imports)
from app.routers import favorites, movies, charts, comparisons

# Include all routers
api_router = APIRouter()
api_router.include_router(movies.router, tags=["movies"])
api_router.include_router(favorites.router, tags=["favorites"])
api_router.include_router(charts.router, tags=["charts"])
api_router.include_router(comparisons.router, tags=["comparisons"])

# Include API router with version prefix
app.include_router(api_router, prefix="/api/v1")
```

These changes improve your API by:
1. Adding proper versioning with `/api/v1/` prefix
2. Restructuring endpoints to follow resource-oriented design
3. Adding HATEOAS links in responses
4. Standardizing pagination parameters
5. Using more descriptive method names (list_*, get_*, create_*)
6. Creating dedicated routers for charts and comparisons