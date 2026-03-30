# TALLER
# Punto-6
# Cargar paquete
library(FinCal)


enunciado <- paste(
  "Suponga que hay un activo en la economía con un retorno de 10% anual.",
  "Imagine dos amigas, Adelaida y Beatriz, que nacieron al mismo tiempo.",
  "Beatriz comenzó a ahorrar desde los 19 años, $2000 USD al inicio de cada año.",
  "Dejó de ahorrar a los 25 años.",
  "Adelaida comenzó a ahorrar a los 26 años y continuó hasta los 55.",
  "¿Cuánto dinero tiene cada una a los 55 años? ",
  sep = "\n"
)

cat(enunciado)

# Datos
r <- 0.10
pago <- 2000

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
cat("Beatriz tiene $", fv_beatriz, " a los 55 años.\n")
cat("Adelaida tiene $", -fv_adelaida, " a los 55 años.\n")
