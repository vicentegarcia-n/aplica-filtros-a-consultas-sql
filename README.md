# aplica-filtros-a-consultas-sql
Proyecto hecho en el curso #4 "Herramientas del oficio: Linux y SQL" del Certificado de Ciberseguridad de Google

### 🗄️ Aplica filtros a consultas SQL

**Descripción:**  
Este proyecto demuestra la aplicación de consultas SQL con filtros para analizar datos de seguridad en una organización. Se utilizó SQL para extraer información específica de las bases de datos relacionadas con intentos de inicio de sesión y equipos de empleados, permitiendo identificar posibles incidentes de seguridad.

**📌 Objetivo del proyecto:**  
- Analizar **intentos de inicio de sesión fallidos** para detectar accesos no autorizados.  
- Filtrar información de empleados según departamento y ubicación.  
- Aplicar operadores SQL (`AND`, `OR`, `NOT`, `LIKE`) para refinar los resultados.  

**🔍 Consultas implementadas:**  

1. **📌 Identificación de intentos de inicio de sesión fallidos fuera del horario laboral:**  
   ```sql
   SELECT *
   FROM log_in_attempts
   WHERE login_time > '18:00' AND success = FALSE;
   ```
     - Permite detectar posibles ataques o accesos indebidos después de la jornada laboral.
  
2. **📅 Filtrar intentos de inicio de sesión en fechas específicas:**
   ```sql
   SELECT *
   FROM log_in_attempts
   WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
   ```
     - Útil para investigar eventos sospechosos en fechas concretas.

3. **🌍 Detectar intentos de inicio de sesión fuera de México:**
   ```sql
   SELECT *
   FROM log_in_attempts
   WHERE NOT country LIKE 'MEX%';
   ```
     - Identifica inicios de sesión desde ubicaciones no autorizadas.

4. **🏢 Recuperar empleados del departamento de Marketing en el edificio Este:**
   ```sql 
   SELECT *
   FROM employees
   WHERE department = 'Marketing' AND office LIKE 'East%';
   ```
     - Filtra empleados de un departamento específico en una sede particular.

5. **💼 Obtener empleados de Finanzas o Ventas:**
   ```sql
   SELECT *
   FROM employees
   WHERE department = 'Finance' OR department = 'Sales';
   ```
     - Agrupa empleados de diferentes departamentos para aplicar medidas de seguridad.

6. **🛑 Excluir empleados del departamento de TI:**
   ```sql
   SELECT *
   FROM employees
   WHERE NOT department = 'Information Technology';
   ```
     - Permite actualizar equipos de todos los empleados excepto los de TI.

**🛠️ Herramientas utilizadas:**  
- SQL (MySQL, PostgreSQL o SQLite) para ejecutar consultas.
- Operadores lógicos (`AND`, `OR`, `NOT`) para filtrar información.
- Expresiones con `LIKE` y comodín `%` para búsquedas flexibles.

**📌 Aprendizajes clave:** 
- Cómo utilizar SQL para extraer información de bases de datos de seguridad.
- Uso de filtros avanzados para detectar patrones de actividad sospechosa.
- Aplicación de operadores lógicos para optimizar consultas.
