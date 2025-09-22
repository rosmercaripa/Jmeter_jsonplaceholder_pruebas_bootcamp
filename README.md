# ⚡ Simulación de Pruebas de Performance sobre un Servicio Público de Consultas

Este proyecto consiste en la simulación y análisis de **pruebas de performance** sobre la API pública **[JSONPlaceholder](https://jsonplaceholder.typicode.com/)**, utilizando **Apache JMeter**.  
El objetivo es evaluar el comportamiento del servicio ante un escenario de carga que emule el uso de usuarios reales.

---

## 🎯 Objetivo

- Configurar un **Plan de Pruebas en JMeter** para validar rendimiento de una API.  
- Simular **40 usuarios concurrentes** con ingreso progresivo y múltiples ciclos de ejecución.  
- Evaluar métricas clave: **tiempos de respuesta, throughput y porcentaje de errores**.  
- Analizar la **estabilidad del servicio** bajo carga controlada.  

---

## 🛠️ Configuración del Plan de Pruebas

### 1. Thread Group
- Número de usuarios (Threads): **40**  
- Ramp-Up Period: **40 segundos** (un usuario por segundo).  
- Loop Count: **3 ciclos**  

### 2. Peticiones HTTP
Se configuraron **3 Samplers HTTP Request** con el servidor `jsonplaceholder.typicode.com`:

- **GET /posts** → Listado de publicaciones.  
- **GET /comments** → Listado de comentarios.  
- **GET /users** → Listado de usuarios.  

### 3. Emulación de Comportamiento Humano
- Se utilizó un **Gaussian Random Timer** con:
  - Retardo promedio: **1200 ms**
  - Desviación estándar: **400 ms**

Esto permite introducir pausas entre peticiones simulando la navegación de un usuario real.  

### 4. Manejo de Sesiones y Cache
- **HTTP Cookie Manager**  
- **HTTP Cache Manager**  

Con esto se emula el comportamiento de un navegador real en cuanto a cookies y cache.  

### 5. Listeners Agregados
- **View Results Tree** (validación de respuestas).  
- **Aggregate Report** (tiempo de respuesta, throughput y errores).  
- **Summary Report** (visión general de resultados).  

---

## ▶️ Ejecución de la Prueba

1. Abrir **Apache JMeter**.  
2. Configurar el plan de pruebas con los elementos mencionados.  
3. Ejecutar con el botón **Start** desde la interfaz GUI.  
4. Observar en tiempo real el rendimiento de las peticiones.  

---

## 📊 Análisis de Resultados

Al finalizar la prueba, los reportes permiten responder:

- **Tiempo de respuesta promedio: 177**  
  Valor observado en **Summary report** (milisegundos).  

- **Errores detectados: 0.00%**  
  ¿Se obtuvieron códigos distintos de `200 OK`? ¿Cuál fue el **% de error** reportado?  

- **Throughput registrado:2.9/sec**  
  Promedio de **peticiones procesadas por segundo**.  

- **Estabilidad del servicio:**  
  Con base en los resultados, determinar si la API respondió de manera **estable** y consistente ante la carga de **40 usuarios concurrentes en 3 ciclos**.  

---

## 📖 Reflexión

Este ejercicio permitió aplicar los conocimientos de **pruebas de performance** en un entorno realista:  

- Se reforzó la importancia de diseñar escenarios con **usuarios concurrentes y ramp-up progresivo**.  
- Se simuló **comportamiento humano** mediante timers, evitando una carga artificial instantánea.  
- Se utilizó el manejo de **sesiones y cache** para reflejar la navegación real en un navegador.  
- Los resultados obtenidos permiten evaluar si un **servicio público como JSONPlaceholder** puede mantenerse estable bajo una carga moderada.  

---

## 👤 Autor

- [Tu Nombre]  
- QA Performance Tester | Automation Engineer  
- [LinkedIn](https://www.linkedin.com/) | [GitHub](https://github.com/TU_USUARIO)
