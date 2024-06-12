# H2 Limieten

## Bijzondere goniometrische limieten

$\lim\limits_{x\rightarrow0}\dfrac{\sin (x)}{x} = 1$
$\lim\limits_{x\rightarrow 0}\dfrac{\tan (x)}{x}=1$
# H3 Afgeleiden
## Basics

- $D(x^n)=nx^{n-1}dx$
- $D(f(x)+g(x))= D(f(x)+ D(g(x))$
- $D(\lambda f)(x)= \lambda D(f(x))$

- $d(f \cdot g)(x) = f(x)g'(x)+f'(x)g(x)$
- $d\left( \dfrac{f(x)}{g(x)}\right) = \dfrac{g(x)f'(x)-g'(x)f(x)}{(g(x))^2}$
## Goniometrische functies

- $D(\sin x)=\cos x$
- $D(\cos x)=-\sin x$
- $D(\tan x)=\dfrac{1}{\cos^2 x}$
- $D(\cot x)=\dfrac{-1}{\sin^2 x}$
- $D(\sec x)=\dfrac{\sin x}{\cos^2 x}$
- $D(\csc x)=\dfrac{-\cos x}{\sin^2 x}$
## Cyclometrische functies

- $D(\arcsin x)=\dfrac{1}{\sqrt{1-x^2}}$
- $D(\arccos x)=\dfrac{-1}{\sqrt{1-x^2}}$
- $D(\arctan x)=\dfrac{1}{1+x^2}$
- $D(\text{arccot } x)=\dfrac{-1}{1+x^2}$
## Hyperbolische functies

- $D(\sinh x)=\cosh x$
- $D(\cosh x)=\sinh x$
- $D(\tanh x)=\dfrac{1}{\cosh^2 x}$
- $D(\coth x)=\dfrac{-1}{\sinh^2 x}$
## Exponentiële functies

- $D(a^x)=a^x \ln a$
- $D(e^x)=e^x$
- $D(\ln x)=\dfrac{1}{x}$
- $D(\log_a x)=\dfrac{1}{x \ln a}$
## Kettingregel

- $D(f(g(x)))=f'(g(x))g'(x)$
## Machtsregel
- $D(f(x)^{g(x)})=g(x)f(x)^{g(x)-1}f'(x)+f(x)^{g(x)}g'(x)\ln f(x)$

# H4 Integralen

## Basics

- $\displaystyle\int x^n dx = \dfrac{x^{n+1}}{n+1}+C$
- $\displaystyle\int f(x)+g(x)dx = \displaystyle\int f(x)dx + \displaystyle\int g(x)dx$
- $\displaystyle\int \lambda f(x)dx = \lambda \displaystyle\int f(x)dx$

- $\displaystyle\int f(x)g'(x)dx = f(x)g(x)-\displaystyle\int f'(x)g(x)dx$
- $\displaystyle\int \dfrac{f'(x)}{f(x)}dx = \ln |f(x)| + C$

## Goniometrische functies

- $\displaystyle\int \sin x dx = -\cos x + C$
- $\displaystyle\int \cos x dx = \sin x + C$
- $\displaystyle\int \dfrac{1}{cos^2 x}= \tan x + C$
- $\displaystyle\int \dfrac{-1}{\sin^2 x}dx = \cot x + C$

## Cyclometrische functies

- $\displaystyle\int \dfrac{1}{\sqrt{1-x^2}}dx = \arcsin x + C$
- $\displaystyle\int \dfrac{1}{\sqrt{a^2-x^2}}dx = \arcsin \dfrac{x}{a} + C$
- $\displaystyle\int \dfrac{1}{x^2+1}dx = \arctan x + C$
- $\displaystyle\int \dfrac{1}{\sqrt{x^2+a}}dx = \ln |x+\sqrt{x^2+a}| + C$

## Hyperbolische functies

- $\displaystyle\int \cosh x dx = \sinh x + C$
- $\displaystyle\int \sinh x dx = \cosh x + C$
- $\displaystyle\int \dfrac{1}{\cosh^2 x}dx = \tanh x + C$
- $\displaystyle\int \dfrac{1}{\sinh^2 x}dx = -\coth x + C$

## Exponentiële functies

- $\displaystyle\int a^x dx = \dfrac{a^x}{\ln a} + C$
- $\displaystyle\int e^x dx = e^x + C$
- $\displaystyle\int \dfrac{1}{x}dx = \ln |x| + C$

# H5 Bepaalde integralen

## Oppervlakte

| Cartesisch | $S=\displaystyle\int_a^b \|f(x)\|dx$                        |
|: ---------- |: ----------------------------------------------------------- |
| Parameter  | $S=\displaystyle\int_a^b \|g(t)\|f'(t)dt$                   |
| Pool       | $S=\displaystyle\int_{\alpha}^{\beta} (r(\theta))^2d\theta$ |

## Omwentelingsvolume

| Cartesisch | $V=\pi \displaystyle\int_a^b (f(x))^2dx$      |
|: ---------- |: --------------------------------------------- |
| Parameter  | $V=\pi \displaystyle\int_a^b (g(t))^2f'(t)dt$ |
| Pool       |                                               |

## Booglengte

| Cartesisch | $L=\displaystyle\int_a^b \sqrt{1+(f'(x))^2}dx$                                    |
|: ---------- |: --------------------------------------------------------------------------------- |
| Parameter  | $L=\displaystyle\int_a^b \sqrt{(f'(t))^2+(g'(t))^2}dt$                            |
| Pool       | $L=\displaystyle\int_{\alpha}^{\beta} \sqrt{(r(\theta))^2+(r'(\theta))^2}d\theta$ |

## Complanatie

| Cartesisch | $C=2\pi \displaystyle\int_a^b \|f(x) \| \sqrt{1+(f'(x))^2}dx$        |
|: ---------- |: -------------------------------------------------------------------- |
| Parameter  | $C=2\pi \displaystyle\int_a^b \|g(t)\| \sqrt{(f'(t))^2+(g'(t))^2}dt$ |
| Pool       |                                                                      |
