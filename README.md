# Pruebas_A-B
Tarea analítica de una tienda en línea internacional. Tus predecesores no consiguieron completarla: lanzaron una prueba A/B y luego abandonaron

# **Proyecto análisis pruebas A/B**

Has recibido una tarea analítica de una tienda en línea internacional. Tus predecesores no consiguieron completarla: lanzaron una prueba A/B y luego abandonaron (para iniciar una granja de sandías en Brasil). Solo dejaron las especificaciones técnicas y los resultados de las pruebas.

**Descripción técnica:**
- Nombre de la prueba: recommender_system_test
- Grupos: А (control), B (nuevo embudo de pago)
- Fecha de lanzamiento: 2020-12-07
- Fecha en la que dejaron de aceptar nuevos usuarios: 2020-12-21
- Fecha de finalización: 2021-01-01
- Audiencia: 15% de los nuevos usuarios de la región de la UE
- Propósito de la prueba: probar cambios relacionados con la introducción de un sistema de recomendaciones mejorado
- Resultado esperado: dentro de los 14 días posteriores a la inscripción, los usuarios mostrarán una mejor conversión en vistas de la página del producto (el evento product_page), instancias de agregar artículos al carrito de compras (product_cart) y compras (purchase). En cada etapa del embudo product_page → product_cart → purchase, habrá al menos un 10% de aumento.
- Número previsto de participantes de la prueba: 6 000


---

# **Solución Propuesta:**

### **1. Configuración Inicial:** 
Cargaremos las librerías necesarias (principalmente pandas para manipulación de datos, numpy para cálculos numéricos, scipy.stats para la prueba z, y matplotlib/seaborn para visualizaciones) y los 4 archivos CSV en DataFrames de pandas.

### **2. Objetivos del Estudio:** 
Formalizaremos los objetivos basados en la descripción (evaluar si el nuevo sistema de recomendación mejora la conversión en product_page, product_card y purchase en al menos un 10% en 14 días).

### **3. Exploración y Limpieza de Datos:**
- Revisaremos los tipos de datos (especialmente fechas) y haremos conversiones si es necesario.
- Buscaremos valores ausentes y duplicados en cada DataFrame y decidiremos cómo manejarlos.
- Importante: Verificaremos la consistencia de los datos. Mencionaste que la audiencia es de la UE, pero los nombres de archivo contienen "us". Revisaremos la columna region en final_ab_new_users_upd_us.csv para confirmar si tenemos datos de usuarios de la UE y filtraremos si es necesario. También filtraremos para asegurarnos de que solo analizamos a los participantes de la prueba recommender_system_test.

### **4. Análisis Exploratorio de Datos (EDA):**
- Construiremos el embudo de conversión (product_page -> product_card -> purchase) para los grupos A y B.
- Analizaremos cómo se distribuyen los eventos por usuario en cada grupo.
- Comprobaremos si hay usuarios asignados incorrectamente a ambos grupos.
- Visualizaremos la distribución de eventos a lo largo del tiempo y la compararemos con posibles eventos de marketing.
- Realizaremos otras verificaciones: ¿Coinciden las fechas de la prueba con los datos? ¿El número de participantes es cercano a 6000? ¿Los usuarios analizados se registraron durante el período correcto (7-21 Dic 2020)?

### **5. Evaluación de la Prueba A/B:**
- Calcularemos las tasas de conversión para cada etapa relevante (product_page, product_card, purchase) para los grupos A y B.
- Utilizaremos pruebas z para proporciones para determinar si las diferencias observadas entre los grupos son estadísticamente significativas (usando un nivel de significancia estándar, α = 0.05).

### **6. Conclusiones:** 
Resumiremos los hallazgos clave del EDA y los resultados de las pruebas A/B, indicando si el grupo B tuvo un rendimiento significativamente mejor y si se cumplieron los objetivos del 10% de aumento.

---
