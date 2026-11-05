# sql-select-fundamentals-

1. ¿Por qué es mala práctica usar SELECT * en producción?
Usar SELECT * en consultas ejecutadas en entornos de producción genera problemas críticos que afectan la estabilidad y eficiencia de los sistemas.

Impacto en el rendimiento (Performance): Traer todas las columnas de una tabla consume más memoria RAM, ancho de banda de red y recursos de I/O en el disco. Además, impide que el motor de la base de datos utilice índices cobertor (covering indexes), ya que el sistema se ve obligado a buscar los datos completos de las filas en lugar de leer únicamente los campos solicitados.

Problemas de mantenibilidad y fragilidad: Si en el futuro se modifica la estructura de la tabla (por ejemplo, se añade una columna pesada de tipo TEXT o se elimina/renombra una columna), todas las consultas que usen SELECT * y dependan de ese orden o cantidad de campos pueden fallar o devolver datos erróneos en aplicaciones y tableros downstream.

Riesgos de seguridad: Expone datos sensibles (como hashes de contraseñas, salarios o información personal identificable) que no deberían viajar por la red ni ser accesibles por procesos o vistas que solo necesitaban un subconjunto inocuo de información.

2. ¿Por qué son importantes los alias para un stakeholder no técnico?
Los alias (AS) son fundamentales porque actúan como un puente traductores entre la arquitectura técnica de la base de datos y el vocabulario de negocio. Los desarrolladores y administradores diseñan las tablas con convenciones técnicas (como snake_case, abreviaturas o nombres en inglés como total_amount), pero un director de finanzas o un analista de negocio necesita ver términos claros y profesionales en su idioma para tomar decisiones rápidas sin confusiones.
