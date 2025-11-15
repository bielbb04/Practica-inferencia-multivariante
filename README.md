# Práctica-inferencia-multivariante

## 📋 Descripción

Este documento contiene ejercicios prácticos de inferencia estadística multivariante implementados en R, correspondientes a la asignatura **23217 - Análisis de Datos para el GMAT**.

Los ejercicios cubren temas fundamentales de estadística multivariante incluyendo:
- Modelos multinomiales
- Regresión multivariante y función score
- Estimación por máxima verosimilitud
- Matriz de información de Fisher
- Contraste de hipótesis de Hotelling T²
- Comparación de medias multivariantes

---

## 📂 Estructura del Documento

### **Problema 1: Modelo Multinomial**
Análisis de preferencias de clientes entre tres productos usando distribución multinomial.

**Contenido:**
- Estimación de parámetros del modelo multinomial
- Cálculo de probabilidades teóricas
- Simulación de muestras aleatorias (1000 repeticiones)
- Comparación entre probabilidades teóricas y frecuencias observadas

**Paquetes necesarios:** Base R

---

### **Problema 2: Regresión Multivariante y Función Score**
Modelización de niveles de contaminación en función de emisiones industriales y densidad de tráfico.

**Contenido:**
- Modelo de regresión: `Y = β₀ + β₁X₁ + β₂X₂ + ε`
- Cálculo de la función score
- Estimación de parámetros β mediante mínimos cuadrados: `β = (X'X)⁻¹X'Y`
- Interpretación en contexto ambiental

**Paquetes necesarios:** `tidyverse`

**Nota:** El documento menciona problemas de singularidad en X'X que requieren consideraciones adicionales.

---

### **Problema 3: Estimación por Máxima Verosimilitud**
Evaluación de la eficacia de un tratamiento médico para reducir la presión arterial.

**Contenido:**

#### a) Estimadores de Máxima Verosimilitud
- Estimación de μ (media poblacional)
- Estimación de σ² (varianza poblacional)
- Datos: disminuciones de presión arterial en 10 pacientes

#### b) Matriz de Información de Fisher
Cálculo e interpretación de la matriz:

```
I(μ, σ²) = [ n/σ²      0     ]
           [   0    n/(2σ⁴)  ]
```

**Interpretación:** La matriz diagonal indica independencia asintótica entre los estimadores de μ y σ².

**Paquetes necesarios:** Base R

---

### **Problema 4: Contraste T² de Hotelling (Una Muestra)**
Verificación si el perfil medio de trabajadores coincide con valores de referencia establecidos.

**Contenido:**
- Generación de muestra bivariante: `X ~ N₂(μ, Σ)`
- Variables: rendimiento (X₁) y satisfacción laboral (X₂)
- Hipótesis: `H₀: μ = μ₀` vs `H₁: μ ≠ μ₀`
- Cálculo del estadístico T² de Hotelling
- Transformación a distribución F
- Cálculo de p-valor y decisión estadística

**Vector de referencia:**
```
μ₀ = [70]
     [ 7]
```

**Paquetes necesarios:** `MASS`

---

### **Problema 5: Comparación de Dos Grupos (T² de Hotelling)**
Comparación del perfil cognitivo entre dos grupos de estudiantes según horas de sueño.

**Contenido:**
- **Grupos:**
  - Grupo 1: Duermen ≥ 8 horas
  - Grupo 2: Duermen < 6 horas
- **Variables medidas:**
  - X₁: Tiempo de reacción (ms)
  - X₂: Puntuación de memoria (0-20)
- **Hipótesis:** `H₀: μ₁ = μ₂` vs `H₁: μ₁ ≠ μ₂`

**Estadístico de contraste:**
```
F = [(n₁+n₂-1-p) / ((n₁+n₂-2)p)] × [(n₁n₂)/(n₁+n₂)] × (x̄-ȳ)'Ŝ⁻¹(x̄-ȳ)
```

donde `Ŝ = (n₁S₁ + n₂S₂)/(n₁+n₂-2)` es la matriz de covarianzas agrupada.

**Resultado:** Se rechaza H₀ con α = 0.05 (p-valor << 0.05)

**Conclusión:** Existe evidencia significativa de que las horas de sueño afectan el perfil cognitivo.

**Paquetes necesarios:** `tidyverse`

---

## 🔧 Requisitos

### Paquetes de R necesarios:
```r
install.packages("tidyverse")
install.packages("MASS")
```

### Software:
- R (≥ 4.0.0)
- RStudio (recomendado)
- Quarto (para renderizar el documento)

---

## 📊 Ejecución

### Renderizar el documento completo:
```r
quarto::quarto_render("practica_inferencia_multivariante.qmd")
```

### Ejecutar chunks individuales:
Abrir el archivo `.qmd` en RStudio y ejecutar cada chunk de código de forma interactiva.

---

## 📈 Conceptos Clave Implementados

1. **Distribución Multinomial**: Modelización de variables categóricas con más de dos categorías
2. **Función Score**: Gradiente de la log-verosimilitud respecto a los parámetros
3. **Matriz de Información de Fisher**: Mide la cantidad de información que los datos contienen sobre los parámetros
4. **Estimadores de Máxima Verosimilitud**: Método de estimación puntual óptimo asintóticamente
5. **T² de Hotelling**: Extensión multivariante de la prueba t de Student
6. **Transformación a F**: Conversión del estadístico T² a distribución F para obtener p-valores

---

## 📝 Notas Importantes

- **Problema 2**: Existe un problema de singularidad en la matriz X'X que requiere atención especial
- **Problema 3**: Se utiliza `n-1` como denominador en el cálculo de varianza (corrección de Bessel)
- **Problemas 4 y 5**: Se asume normalidad multivariante y homocedasticidad (igualdad de matrices de covarianza)
- Todos los contrastes se realizan con nivel de significación **α = 0.05**

---

## 👨‍🎓 Autor

Ejercicios correspondientes a la asignatura 23217 - Análisis de Datos para el GMAT

---

## 📄 Licencia

Material educativo para uso académico.
