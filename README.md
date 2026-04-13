# 📦 Optimización Logística Olist: Segmentación Geográfica para CVRP en São Paulo

Este repositorio contiene el desarrollo del Desafío Analítico para la asignatura de **ML No Supervisado (2026-I)**. El proyecto aplica técnicas de aprendizaje automático, inferencia estadística y simulación para optimizar la logística de entrega en el estado de São Paulo, Brasil.

## 👥 Información del Estudiante
* **Nombre:** Sofía Núñez Rodrigue
* **Código:** 0000326111
* **Carrera:** Ciencia de Datos — 5.° Semestre
* **Institución:** Universidad de La Sabana

---

## 🎯 Pregunta de Negocio
**¿Cómo pueden agruparse los clientes de São Paulo por zona geográfica para minimizar la distancia total recorrida por la flota de entrega (Capacitated Vehicle Routing Problem - CVRP)?**

### 📊 Justificación de Datos
Se integraron **6 de los 9 archivos** del [Olist Dataset en Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), permitiendo una visión 360° del problema:
- `orders` & `order_items`: Ciclo de vida y métricas de retraso.
- `products`: Peso del paquete (**Variable clave MLE** y restricción de capacidad).
- `customers` & `sellers`: Georreferenciación de origen y destino.
- `geolocation`: Coordenadas lat/lng para cálculo de distancias reales (**Haversine**).

---

## 🛠️ Tecnologías y Metodología

El análisis se divide en cuatro pilares técnicos fundamentales:

### 1. Estimación de Máxima Verosimilitud (MLE)
Se analizó la distribución del peso de los productos para entender la demanda física. 
- **Distribución Ganadora:** Log-Normal (AIC: 1,446,145 / BIC: 1,446,164).
- **Parámetros:** $\mu = 5.92$, $\sigma = 1.35$.

### 2. Inferencia Bayesiana
Evaluación de la probabilidad de retraso en las entregas de São Paulo.
- **Prior:** Basado en datos históricos 2017-H1 (Distribución Beta).
- **Posterior:** Se estimó una tasa de retraso del **8.71%**, con un intervalo de credibilidad del 95% entre [8.52%, 8.91%].

### 3. Clustering Geográfico (K-Means)
Zonificación logística de clientes en São Paulo utilizando métricas de validación robustas:
- **Silueta:** 0.7895
- **Davies-Bouldin:** 0.5193
- **Calinski-Harabasz:** 10,636.8
- **Resultado:** División óptima en **2 macro-zonas**, reduciendo la complejidad de las rutas y permitiendo una gestión de flota diferenciada.

### 4. Simulación Monte Carlo
Validación estadística de la solución propuesta.
- **Iteraciones:** 5,000.
- **Resultado:** La solución optimizada se ubicó en el **percentil 0** de la distribución de costos aleatorios.
- **Impacto:** Reducción del **62.1%** en los costos operativos proyectados (de R$ 1.63M a R$ 0.61M).

---

## 📂 Estructura del Repositorio
* `examen2.ipynb`: Cuaderno principal con el código en Python comentado y ejecutado.
* `data/`: (Opcional) Espacio para los archivos CSV procesados.

## 🚀 Cómo ejecutar
1. Clonar el repositorio.
2. Asegurarse de tener instaladas las librerías: `pandas`, `numpy`, `scipy`, `sklearn`, `matplotlib`, `seaborn`.
3. Ejecutar las celdas del notebook en orden secuencial.

---
**Fecha de entrega:** 13 de abril de 2026.
