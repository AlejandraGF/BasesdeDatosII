# Bases de datos II - Prueba corta #1
###### Estudiante: Alejandra González - 2020035049

---

1. Explique en que consisten los siguientes conceptos:
    - Data Warehouse: Se usa como un tipo de repositorio que suele utilizar las empresas para "depositar" y almacenar diferentes tipos de datos.
    - Data Lake: Tipo de repositorio que permite almacenar grandes cantidades de datos de forma cruda(su formato original), estos datos pueden ser estructurados o no.
    - Data Mart: Data mart es un tipo más específico de data warehouse, suele concentrarse en una parte específica de la empresa.

2. De que forma se benefician las aplicaciones del uso de Columnar Storage?                                     
La forma de Columnar Storage es más rápido en comparación con uno orientado al Row Storage porque tienen que leer solo aquellas columnas a las que se accede, en el columnar storage las columnas de tamaño fijo van de primero. Ejemplo: Si tenemos una base de datos de estudiantes en forma de row los resultados de una búsqueda serian "Estudiante 1: nombre, apellido,carné, direccion" y así con la cantidad n de estudiantes en la base de datos. Si la BD está en forma de columnar todos los nombres aparecerían en la columna de "nombre" y todos los apellidos en  "apellido" esto permite mantener los datos más cerca y todos los datos de una columna van a pertenecer al mismo tipo de dato lo cual mejora el rendimiento.

3. ¿En que consiste streaming y batch processing?
- El streaming data son datos que se capturan en tipo real, estos datos son almacenan y procesan continuamente. Este tipo de data le permite a las empresas conocer más sobre la actividad de sus clientes. Ejemplo: los clics de una página web, la ubicación de un dispositivo, facturación, etc.
- Batch processing: Consiste en extraer datos de múltiples fuentes para cargarlos en sistemas de data warehouse.Existen varios tipos: 
    -   Extract Transform Load (ETL): Consiste en extraer los datos, pasarlos por un proceso de formateo o limpia para luego ingresarlos al data warehouse.
    -   Extract Load Transform (ELT): En esta forma de batch processing se extrae los datos, se ingresan al data warehouse y luego se les aplica la transformación.


4. ¿En que consiste datos estructurados, semi estructurados y no estructurados?
- Estructurados: son aquellos que se encuentran ordenados o que todos cumplen con cierto formato. Suelen venir de una base de datos.
- Semi-estructurados: Datos donde no todos tienen los mismos atributos. Ejemplo: archivos Json, archivos UML.
- No estructurados: Datos sin ningún patrón. Ejemplo: texto, audio ,video.
   
   
   
  
