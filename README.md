# TALLER - Punto 6

## Problema Financiero: Valor Futuro de Inversiones

### Enunciado del Problema

Suponga que hay un activo en la economía con un retorno de 10% anual.

Imagine dos amigas, **Adelaida** y **Beatriz**, que nacieron al mismo tiempo:

- **Beatriz** comenzó a ahorrar desde los 19 años, $2000 USD al inicio de cada año.
- Dejó de ahorrar a los 25 años.
- **Adelaida** comenzó a ahorrar a los 26 años y continuó hasta los 55.

**Pregunta:** ¿Cuánto dinero tiene cada una a los 55 años?

---

## Solución en R

```r
# Cargar paquete
library(FinCal)

# Datos
r <- 0.10      # Tasa de retorno anual (10%)
pago <- 2000   # Pago anual en USD

# =========================
# BEATRIZ
# =========================
# Aporta 7 años (19 a 25)
fv_beatriz_25 <- fv.annuity(r = r, n = 7, pmt = pago, type = 1)

# Ese dinero crece desde 25 hasta 55 → 30 años
fv_beatriz <- fv.simple(r = r, n = 30, pv = fv_beatriz_25)

# =========================
# ADELAIDA
# =========================
# Aporta de 26 a 55 → 30 años
fv_adelaida <- fv.annuity(r = r, n = 30, pmt = pago, type = 1)

# =========================
# RESULTADOS
# =========================
cat("Beatriz tiene $", round(fv_beatriz, 2), " a los 55 años.\n")
cat("Adelaida tiene $", round(fv_adelaida, 2), " a los 55 años.\n")
```

---

## Análisis de Resultados

El ejercicio demuestra un concepto financiero importante: **el poder del tiempo en las inversiones**.

- **Beatriz** aprovechó el tiempo realizando aportaciones tempranas, aunque fueron por menos años. Su dinero tuvo 30 años para crecer al 10% anual.
- **Adelaida** realizó aportaciones durante más años (30), pero comenzó más tarde.

### Conclusión

Este ejercicio ilustra por qué es importante comenzar a ahorrar desde temprano, incluso si los montos iniciales son pequeños. El interés compuesto favorece a quien comienza antes, permitiendo que el dinero trabaje durante más tiempo.