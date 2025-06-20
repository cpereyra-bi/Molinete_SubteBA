Utilizamos datos abiertos del Gobierno de la Ciudad de Buenos Aires que registran la cantidad de pasajeros por molinete, discriminados por tipo de pasaje, en franjas de 15 minutos durante el año 2024.

---

## Dataset utilizado: [Buenos Aires Data - Subte: Molinetes 2024](https://data.buenosaires.gob.ar/dataset/subte-viajes-molinetes/resource/9faf4137-63c9-4f15-848c-248c166b54ea)

**Descripción de la base de datos:**
- Cantidad de pasajeros por molinete, por estación y por tipo de pasaje.
- Intervalos de 15 minutos.
- Datos correspondientes al Diciembre/2024.

**Campos principales:**
| Campo             | Tipo     | Descripción                                      |
|------------------|----------|--------------------------------------------------|
| `fecha`          | date     | Fecha del registro                               |
| `desde`          | time     | Hora de inicio del intervalo                     |
| `hasta`          | time     | Hora de finalización del intervalo               |
| `linea`          | string   | Línea de subte                                   |
| `molinete`       | string   | Código del molinete                              |
| `estacion`       | string   | Estación del subte                               |
| `pax_total`      | integer  | Total de pasajeros que usaron el molinete        |

---

## 🛠️ Actividades Realizadas

### 1. Configuración Inicial

- Se creó un nuevo archivo `.pbix` desde Power BI Desktop.
- Se deshabilitó la detección automática de:
  - Relaciones.
  - Tablas de fechas.
- Se creó una tabla de medidas clave para centralizar los KPIs del modelo.

### 2. Tabla de Fechas

- Se copió y pegó código M personalizado para generar una tabla de fechas extendida (año, mes, semana, día, etc.).
- Se configuró el rango dinámico de fechas en base a la tabla de datos original.

- 📄 Script de la **Tabla de Tiempos (horas)**:  
  [Ver código M - tabla_tiempos.m](./tabla_tiempos.m)

### 3. Tabla de Tiempos

- Se generó una tabla de tiempos para representar intervalos de 15 minutos.
- Incluye hora, minuto, franja horaria, etc.
- Se utilizó código M para construirla desde cero.

### 4. Carga y Transformación de Datos

- Se cargó el archivo CSV contenido en el ZIP descargado desde el portal de datos.
- Se transformaron y renombraron columnas para facilitar la lectura.
- Se creó una nueva columna de tipo datetime uniendo `fecha` y `desde`.
- Se categorizaron franjas horarias (mañana, tarde, noche).
- Se cambió el tipo de datos para permitir relaciones futuras.

### 5. Modelado

- Se establecieron relaciones entre:
  - Tabla de hechos (`molinetes_2024`)
  - Tabla de fechas
  - Tabla de tiempos
- Se organizó el modelo en carpetas temáticas para visualizaciones futuras.
- Se validó la integridad del modelo con vistas previas.

---

## 📌 Notas adicionales

- Este proyecto sienta las bases para el análisis exploratorio de flujos de pasajeros en estaciones clave y horarios pico.
- Se puede extender con segmentaciones por estación, línea o tipo de pasaje.
- Ideal para identificar patrones de uso del transporte público en CABA.
