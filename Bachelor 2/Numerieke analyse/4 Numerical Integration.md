## 4.1 Trapeziumregel en Basisconcepten
**Kernidee**: Benader de integraal $I = \int_{\alpha}^{\beta} f(t)\,dt$ door $f$ te interpoleren met een lineair polynoom $P(t)$ over $[\alpha, \beta]$.  
- **Formule**: $\bar{I} = \frac{h}{2}(y_0 + y_1)$ met $h = \beta - \alpha$, $y_0 = f(\alpha)$, $y_1 = f(\beta)$.  
- **Foutanalyse**: Als $f$ tweemaal continu differentieerbaar is, geldt $\bar{I} - I = \frac{1}{12}f''(\tau)h^3$ voor een $\tau \in [\alpha, \beta]$.  

**Voorbeeld**: Voor $\int_0^1 e^{-t^2}\,dt$ geeft de trapeziumregel $\bar{I} = 0.6839$ met foutgrenzen $-\frac{1}{6} \leq \bar{I} - I \leq \frac{1}{12}$.  

## 4.2 Regel van Simpson
**Kernidee**: Verhoog de nauwkeurigheid door een kwadratisch interpolerend polynoom te gebruiken over drie punten.  
- **Formule**: $\bar{I} = \frac{h}{3}(y_0 + 4y_1 + y_2)$ met $h = (\beta - \alpha)/2$.  
- **Foutanalyse**: Voor vier keer differentieerbare $f$: $\bar{I} - I = \frac{1}{90}f^{(4)}(\tau)h^5$.  

**Voorbeeld**: Zelfde integraal geeft $\bar{I} = 0.747180$ met scherpere foutgrenzen $-\frac{1}{144} \leq \bar{I} - I \leq \frac{1}{240}$.  

## 4.3 Uitgebreide Methoden
### Uitgebreide Trapeziumregel
**Kernidee**: Verdeel $[\alpha, \beta]$ in $n$ subintervallen en pas de trapeziumregel lokaal toe.  
- **Formule**: $\bar{I} = h\left(\frac{1}{2}y_0 + \sum_{i=1}^{n-1} y_i + \frac{1}{2}y_n\right)$.  
- **Fout**: $\bar{I} - I = \frac{\beta - \alpha}{12}f''(\sigma)h^2$, convergentiesnelheid $\mathcal{O}(n^{-2})$.  

**Voorbeeld**: Voor $n=512$ is de fout $\leq 3.2 \times 10^{-7}$.  

### Uitgebreide Simpsonregel
**Kernidee**: Combineer Simpsonregels over subintervallen (even $n$).  
- **Formule**: $\bar{I} = \frac{h}{3}\left(y_0 + 2\sum_{j=1}^{m-1} y_{2j} + 4\sum_{j=1}^{m} y_{2j-1} + y_n\right)$.  
- **Fout**: $\bar{I} - I = \frac{\beta - \alpha}{180}f^{(4)}(\sigma)h^4$, convergentiesnelheid $\mathcal{O}(n^{-4})$.  

**Voorbeeld**: Voor $n=512$ is de fout $\leq 9.8 \times 10^{-13}$.  

## 4.4 Extrapolatie naar $h=0$ (Romberg-methode)
**Kernidee**: Versnel convergentie door fouttermen in $T(h)$ te elimineren via lineaire combinaties.  
- **Euler-MacLaurin Formule**: $T(h) = I + \gamma_1 h^2 + \gamma_2 h^4 + \cdots$.  
- **Extrapolatiestappen**:  
  - Bereken $T_{ij} = T_{i,j-1} + \frac{1}{4^j - 1}(T_{i,j-1} - T_{i-1,j-1})$.  
- **Resultaat**: Snellere nauwkeurigheid (bijv. 12 decimalen voor $n=32$).  

**Voorbeeld**: Romberg-tabel toont snelle convergentie vergeleken met uitgebreide Simpson.  

## Key Points to Remember
- **Trapeziumregel → Lineaire interpolatie**: Eenvoudig maar lage nauwkeurigheid ($\mathcal{O}(h^3)$). ★★★☆☆  
- **Simpsonregel → Kwadratische interpolatie**: Exact voor polynomen ≤ graad 3, hogere nauwkeurigheid ($\mathcal{O}(h^5)$). ★★★★☆  
- **Uitgebreide methoden → Herhaalde toepassing**: Verdubbeling van $n$ verkleint fout met factor 4 (trapezium) of 16 (Simpson). ★★★★★  
- **Extrapolatie → Romberg-methode**: Combineert trapeziumwaarden voor exponentieel betere nauwkeurigheid. ★★★★★  
- **Foutanalyse → Afhankelijk van afgeleiden**: Trapezium vereist $f''$, Simpson vereist $f^{(4)}$. ★★★☆☆  