# Proyecto de Detección de Anomalías en Logs de Servidores Web con Big Data

**Autor:** Equipo MLDS – Universidad Nacional de Colombia  
**Integrantes:**  
- Eduar Mauricio Mendez Mendez  
- Sergio Alejandro Rubiano Bautista  
- Sebastián Rodríguez Muñoz  

---

## 📌 Objetivo del proyecto

Desarrollar una **plataforma escalable** que permita la ingesta, almacenamiento y análisis de logs de servidores web (Apache, Nginx, etc.) utilizando tecnologías Big Data, con el fin de **detectar automáticamente comportamientos anómalos** (picos de errores, caídas de tráfico, posibles ataques DDoS, etc.) a partir de métricas agregadas por ventanas de tiempo.

El proyecto combina:

- **Data Lake** (MongoDB) para almacenar logs crudos sin transformación.
- **Data Warehouse** (PostgreSQL) para datos estructurados y agregaciones analíticas.
- **Procesamiento ETL** con Python.
- **Modelo de Machine Learning no supervisado** (Isolation Forest o reglas estadísticas) para identificar anomalías en series temporales.

---

## 📂 Estructura del repositorio

## 📘 Fase 1 – Entendimiento del negocio y arquitectura  
**Archivo:** `Fase1.ipynb`

Contiene:
- **Trasfondo del negocio:** beneficiarios (DevOps, SOC, administradores) y desafíos (volumen, velocidad, falsos positivos).
- **Alcance:** qué incluye (ingesta batch, almacenamiento dual MongoDB+PostgreSQL, extracción de características, modelo de anomalías) y qué excluye (streaming puro, dashboards interactivos).
- **Plan de trabajo:** diagrama de Gantt de 5 semanas.
- **Arquitectura de la solución:** Data Lake (MongoDB) + Data Warehouse (PostgreSQL) + ETL en Python + modelo Isolation Forest.
- **Restricciones y escalabilidad:** requisitos funcionales/no funcionales y estrategias de crecimiento.

---

## ⚙️ Fase 2 – Definición e implementación de las tecnologías  
**Archivo:** `Fase2_Tecnologias.ipynb`

Esta fase ya está **completada** e incluye:

### ✅ Tecnologías seleccionadas y justificación
- **Apache Spark** – lectura de dataset en Parquet (grande para pandas en Colab).
- **MongoDB Atlas** – Data Lake ligero (aunque en el código se usa MongoDB local).
- **PostgreSQL** – Data Warehouse para consultas analíticas.
- **Python + scikit-learn** – limpieza, features y modelo de anomalías.
- **Google Colab** – entorno gratuito de desarrollo.
- **Framework de visualización** – gráficos en el propio notebook.

Se incluye una tabla comparativa con alternativas (pandas, Cassandra, Elasticsearch, etc.) y las ventajas/limitaciones de cada tecnología.

### ✅ Metodología de resolución
Se describe el pipeline paso a paso:
1. Lectura del Parquet con Spark.
2. Almacenamiento de métricas relevantes en MongoDB.
3. Transformación y carga a PostgreSQL.
4. Agregación temporal (por minuto) vía SQL.
5. Entrenamiento de Isolation Forest.
6. Generación de alertas y visualización.

### ✅ Instalación de herramientas (código funcional)
- Instalación de **MongoDB** en Colab (script completo con `wget`, `apt-get`, `mongod`).
- Instalación del driver `pymongo`.
- Prueba de conexión e inserción de un documento de prueba (ejecutada con éxito).
- *Nota:* La instalación de Spark y PostgreSQL se describe pero no se incluye el código (se deja como trabajo futuro o se asume que ya están disponibles en el entorno).

### ✅ Listado de componentes y scripts
Se mencionan los scripts necesarios: ETL, agregaciones SQL, entrenamiento del modelo y alertas.

---

## 🚀 ¿Cómo usar este repositorio?

1. **Clonar**  
   ```bash
   git clone https://github.com/edmendezjob/BigData.git
   cd proyecto-bigdata-anomalias 

