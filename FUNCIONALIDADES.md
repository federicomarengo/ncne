# Documentación de Funcionalidades - Sistema Club Náutico Embalse

**Última actualización:** Noviembre 2025

Este documento describe en detalle todas las funcionalidades implementadas en el sistema de gestión del Club Náutico Embalse. Está diseñado para ser entendido tanto por desarrolladores como por usuarios finales.

---

## Tabla de Contenidos

1. [Dashboard Principal](#dashboard-principal)
2. [Gestión de Socios](#gestión-de-socios)
3. [Gestión de Visitas](#gestión-de-visitas)
4. [Gestión de Embarcaciones](#gestión-de-embarcaciones)
5. [Sistema de Facturación](#sistema-de-facturación)
6. [Conciliación Bancaria](#conciliación-bancaria)
7. [Portal de Autogestión para Socios](#portal-de-autogestión-para-socios)
8. [Configuración del Sistema](#configuración-del-sistema)

---

## Dashboard Principal

### Descripción General
El Dashboard es la pantalla principal del sistema que muestra un resumen ejecutivo de las métricas más importantes del club.

### Funcionalidades Implementadas

#### 1. Métricas Principales
- **Socios Activos**: Total de socios activos del club con incremento del mes
- **Ingresos del Mes**: Muestra el total de ingresos recibidos en el mes corriente con comparación vs mes anterior
- **Embarcaciones**: Total de embarcaciones registradas con nuevas registradas del mes

#### 2. Navegación Rápida
- Menú de acceso directo a los módulos principales:
  - Gestión de Socios
  - Gestión de Embarcaciones
  - Facturación (cobros y pagos)
  - Conciliación Bancaria

#### 3. Gráficos y Visualizaciones
- Gráfico de ingresos mensuales con tendencias
- Botón "Ver Detalles" para información expandida

#### 4. Acciones Rápidas
- Botones de acceso directo para acciones frecuentes:
  - **Nuevo Socio**: Abre el módulo de gestión de socios
  - **Generar Cupones**: Acceso directo a generación masiva de cupones
  - **Conciliar Pagos**: Abre el módulo de conciliación bancaria
  - **Portal de Socios**: Acceso al portal de autogestión para socios

### Acceso
- URL: `dashboard.html`
- Acceso desde el menú principal de navegación

---

## Gestión de Socios

### Descripción General
Módulo completo para administrar toda la información de los socios del club, incluyendo sus datos personales, estados, movimientos financieros y visitas.

### Funcionalidades Implementadas

#### 1. Listado de Socios

**Características:**
- Tabla con todos los socios registrados
- Columnas mostradas:
  - ID del socio
  - Nombre completo
  - DNI
  - Email
  - Teléfono
  - Estado (Activo, Inactivo, Pendiente)
  - Fecha de ingreso
  - Acciones disponibles

**Filtros Disponibles:**
- Búsqueda por nombre, apellido o DNI
- Filtro por estado (Activo, Inactivo, Pendiente)
- Filtro por fecha de ingreso

**Acciones por Socio:**
- **Ver Detalle** (botón azul): Abre el modal de detalle de cuenta del socio
- **Cargar Visita** (botón naranja): Abre el modal de carga de visita con el socio pre-seleccionado
- **Editar** (botón gris): Permite modificar los datos del socio
- **Eliminar** (botón rojo): Elimina el socio del sistema (con confirmación)

#### 2. Detalle de Cuenta del Socio

**Acceso:**
- Desde el botón "Ver" en la tabla de socios
- Desde el botón "Cargar Visita" en el modal de detalle

**Información Mostrada:**

**a) Datos del Socio:**
- Nombre completo
- DNI
- Email
- Teléfono

**b) Resumen de Cuenta:**
- **Deuda Total**: Suma de todos los cupones y cobros pendientes
- **Pagado**: Total de pagos recibidos
- **Pendientes**: Cantidad de items pendientes de pago

**c) Historial de Movimientos:**
Todos los movimientos financieros del socio unificados en una sola lista histórica, con filtros para categorizar:

- **Filtros disponibles:**
  - Todos: Muestra todos los movimientos
  - Cupones: Solo cupones generados
  - Pagos: Solo pagos registrados
  - Visitas: Solo cobros por visitas

**Tipos de Movimientos:**

1. **Cupones:**
   - Fecha de generación
   - Concepto (ej: "Cupón Mensual - Octubre 2025")
   - Número de cupón
   - Fecha de vencimiento
   - Monto
   - Estado (Pendiente, Pagado, Vencido)

2. **Pagos:**
   - Fecha del pago
   - Concepto (ej: "Pago de Cupón N° 00001295")
   - Método de pago
   - Detalle (ej: "Transferencia bancaria - Conciliado")
   - Monto
   - Estado de conciliación

3. **Visitas:**
   - Fecha de la visita
   - Cantidad de visitantes
   - Monto cobrado
   - Estado (Pendiente, Con cupón generado)

**Acciones en el Detalle:**
- **Cargar Visita**: Abre el modal para cargar una nueva visita para este socio
- **Exportar Resumen**: Genera un PDF con el resumen de cuenta
- **Generar Cupón**: Permite generar un cupón manual para el socio
- **Cerrar**: Cierra el modal

#### 3. Alta/Edición de Socios

**Modal de Nuevo Socio:**
- Formulario con los siguientes campos:
  - Nombre completo (requerido)
  - DNI (requerido)
  - Email (requerido)
  - Teléfono (requerido)
  - Dirección
  - Observaciones

**Validaciones:**
- Campos requeridos deben estar completos
- Formato de email válido
- DNI único en el sistema

#### 4. Tabs de Navegación
- **Tab "Socios"**: Muestra el listado y gestión de socios
- **Tab "Visitas"**: Muestra la gestión de todas las visitas (ver sección Gestión de Visitas)

### Flujo de Trabajo Típico

1. **Ver información de un socio:**
   - Usuario busca el socio en la tabla
   - Hace clic en "Ver" (botón azul con icono de ojo)
   - Se abre el modal con el detalle completo
   - Puede filtrar movimientos por tipo (Cupones, Pagos, Visitas)

2. **Cargar una visita:**
   - Desde el listado: Clic en "Cargar Visita" del header
   - Desde el detalle: Clic en "Cargar Visita" dentro del modal de detalle
   - Se abre el modal de carga de visita
   - Se completa el formulario y se guarda

3. **Editar un socio:**
   - Clic en "Editar" (botón con icono de lápiz)
   - Se abre el modal con los datos pre-cargados
   - Se modifican los campos necesarios
   - Se guarda

### Acceso
- URL: `socios.html`
- Acceso desde el menú principal de navegación

---

## Gestión de Visitas

### Descripción General
Sistema para registrar y gestionar las visitas que los socios traen al club. Cada visita tiene un costo fijo configurado y se genera un cobro que se incluye en el cupón mensual.

### Funcionalidades Implementadas

#### 1. Carga de Visitas

**Acceso:**
- Botón "Cargar Visita" (icono naranja) en las acciones de cada socio en la tabla
- Botón "Cargar Visita" dentro del modal de detalle de cuenta del socio

**Modal de Carga de Visita:**

**Campos del Formulario:**

1. **Socio** (Requerido):
   - **Cuando se abre desde la tabla de socios**: El socio ya está pre-seleccionado y bloqueado (no se puede cambiar)
   - **Cuando se abre desde el detalle de cuenta**: El socio ya está pre-seleccionado del modal de detalle
   - Campo muestra el nombre del socio
   - Se muestra el resumen de visitas del mes automáticamente

2. **Fecha de la Visita** (Requerido):
   - Selector de fecha (date picker)
   - Por defecto muestra la fecha actual
   - Permite seleccionar fechas pasadas o futuras

3. **Cantidad de Visitas** (Requerido):
   - Campo numérico
   - Valor mínimo: 1
   - Valor por defecto: 1
   - Al cambiar, se recalcula automáticamente el total

4. **Costo por Visita** (Solo lectura):
   - Muestra el costo configurado en el sistema
   - Valor fijo: $5,000 (configurable)
   - No se puede modificar desde este formulario

5. **Total** (Solo lectura):
   - Se calcula automáticamente: Cantidad × Costo por Visita
   - Se actualiza en tiempo real al cambiar la cantidad
   - Formato: $XX,XXX

6. **Resumen del Mes** (Se muestra al seleccionar socio):
   - Total de visitas cargadas en el mes seleccionado
   - Total acumulado en pesos
   - Cantidad de visitas pendientes vs. con cupón generado
   - Se actualiza automáticamente al cambiar la fecha

7. **Observaciones** (Opcional):
   - Campo de texto libre
   - Permite agregar notas adicionales sobre la visita

**Validaciones:**
- Socio ya está pre-seleccionado al abrir el modal desde las acciones
- Fecha es requerida
- Cantidad debe ser mayor a 0
- El sistema valida que el socio exista antes de guardar

**Acciones:**
- **Cancelar**: Cierra el modal sin guardar
- **Guardar Visita**: Guarda la visita y la registra en el sistema

#### 2. Listado y Gestión de Visitas

**Acceso:**
- Tab "Visitas" en la página de Socios

**Tabla de Visitas:**

**Columnas:**
- Socio: Nombre del socio
- Fecha: Fecha de la visita (formato DD/MM/YYYY)
- Cantidad: Número de visitantes
- Monto: Total cobrado (Cantidad × Costo por visita)
- Estado: Badge visual
  - "Pendiente" (amarillo): Aún no tiene cupón generado
  - "Con cupón" (verde): Ya tiene cupón generado
- Fecha Cupón: Fecha en que se generó el cupón (si aplica)
- Observaciones: Notas adicionales
- Acciones: Botones según el estado

**Filtros Disponibles:**
- **Buscar Socio**: Búsqueda por nombre o DNI del socio
- **Mes**: Filtro por mes (Enero a Diciembre)
- **Estado**: 
  - Todos los estados
  - Pendiente
  - Con cupón generado

**Acciones por Visita:**

**Si el estado es "Pendiente":**
- **Editar** (botón azul): Permite modificar la visita
  - Se abre el modal de carga con los datos pre-cargados
  - Se pueden modificar: socio, fecha, cantidad, observaciones
  - Al guardar, se actualiza la visita existente
- **Eliminar** (botón rojo): Elimina la visita
  - Muestra confirmación antes de eliminar
  - Solo se puede eliminar si está pendiente

**Si el estado es "Con cupón generado":**
- No hay acciones disponibles
- Se muestra el texto "No disponible" en gris
- La visita no se puede editar ni eliminar porque ya fue incluida en un cupón

#### 3. Edición de Visitas

**Proceso:**
1. Usuario hace clic en "Editar" en una visita pendiente
2. Se abre el modal de carga con los datos pre-cargados:
   - Socio seleccionado
   - Fecha de la visita
   - Cantidad de visitas
   - Observaciones
3. Usuario modifica los campos necesarios
4. El total se recalcula automáticamente
5. Al guardar, se actualiza la visita existente (no se crea una nueva)

**Restricciones:**
- Solo se puede editar si el estado es "Pendiente"
- Si la visita ya tiene cupón generado, aparece un mensaje de error

#### 4. Eliminación de Visitas

**Proceso:**
1. Usuario hace clic en "Eliminar" en una visita pendiente
2. Se muestra un diálogo de confirmación con:
   - Fecha de la visita
   - Nombre del socio
3. Si confirma, la visita se elimina del sistema
4. La tabla se actualiza automáticamente

**Restricciones:**
- Solo se puede eliminar si el estado es "Pendiente"
- Si la visita ya tiene cupón generado, aparece un mensaje de error

#### 5. Integración con Facturación

**Generación de Cupones:**
- Cuando se genera el cupón mensual masivo, todas las visitas pendientes del mes se incluyen automáticamente
- Una vez incluida en el cupón, la visita cambia su estado a "Con cupón generado"
- La fecha de generación del cupón se registra en la visita

**Cálculo del Monto:**
- El monto de cada visita se calcula: Cantidad × Costo por Visita
- El costo por visita es fijo y configurado en el sistema ($5,000)
- El total de visitas del mes se suma al cupón mensual del socio

### Flujo de Trabajo Típico

1. **Cargar una nueva visita:**
   - Usuario busca el socio en la tabla
   - Hace clic en el botón "Cargar Visita" (naranja) en las acciones del socio
   - Se abre el modal con el socio ya pre-seleccionado
   - Ingresa la fecha de la visita
   - Ingresa la cantidad de visitantes
   - El sistema calcula automáticamente el total y muestra el resumen del mes
   - Opcionalmente agrega observaciones
   - Guarda la visita

2. **Ver todas las visitas:**
   - Usuario hace clic en la tab "Visitas"
   - Ve la tabla con todas las visitas
   - Puede filtrar por socio, mes o estado
   - Puede editar o eliminar visitas pendientes

3. **Editar una visita:**
   - Usuario hace clic en "Editar" en una visita pendiente
   - Modifica los campos necesarios
   - Guarda los cambios

4. **Eliminar una visita:**
   - Usuario hace clic en "Eliminar" en una visita pendiente
   - Confirma la eliminación
   - La visita se elimina del sistema

### Configuración

**Costo por Visita:**
- Valor configurado: $5,000
- Se puede modificar desde la configuración del sistema
- Afecta a todas las visitas nuevas
- Las visitas ya cargadas mantienen su monto original

### Acceso
- URL: `socios.html` (tab "Visitas")
- Acceso desde el header de Socios o desde el detalle de cuenta

---

## Gestión de Embarcaciones

### Descripción General
Módulo para registrar y gestionar todas las embarcaciones asociadas a los socios del club.

### Funcionalidades Implementadas

#### 1. Listado de Embarcaciones

**Características:**
- Tabla con todas las embarcaciones registradas
- Columnas mostradas:
  - Matrícula
  - Nombre de la embarcación
  - Socio propietario
  - Tipo
  - Eslora
  - Estado
  - Acciones disponibles

**Filtros Disponibles:**
- Búsqueda por matrícula, nombre o socio
- Filtro por tipo de embarcación
- Filtro por estado

**Acciones por Embarcación:**
- **Ver**: Muestra el detalle completo de la embarcación
- **Editar**: Permite modificar los datos
- **Eliminar**: Elimina la embarcación del sistema

#### 2. Alta/Edición de Embarcaciones

**Modal de Nueva Embarcación:**
- Formulario con campos:
  - Matrícula (requerido)
  - Nombre de la embarcación (requerido)
  - Socio propietario (selector, requerido)
  - Tipo (requerido)
  - Eslora (requerido)
  - Manga
  - Calado
  - Año de construcción
  - Motor (información del motor)
  - Observaciones

**Validaciones:**
- Matrícula única en el sistema
- Socio debe existir
- Campos requeridos completos

### Acceso
- URL: `embarcaciones.html`
- Acceso desde el menú principal de navegación

---

## Sistema de Facturación

### Descripción General
Módulo completo para gestionar la facturación del club, incluyendo la generación masiva de cupones mensuales, registro de pagos y seguimiento de transacciones.

### Funcionalidades Implementadas

#### 1. Gestión de Cupones

**Listado de Cupones:**
- Tabla con todos los cupones generados
- Columnas:
  - Número de cupón
  - Socio
  - Concepto
  - Fecha de vencimiento
  - Monto
  - Estado (Pendiente, Pagado, Vencido)
  - Acciones

**Filtros:**
- Buscar por socio (nombre o DNI)
- Por estado (Pendiente, Pagado, Vencido)
- Por rango de fechas (desde/hasta)

**Acciones por Cupón:**
- **Ver** (icono de ojo, botón azul): Muestra el detalle completo del cupón
- **Enviar por Email** (icono de sobre, botón amarillo): Envía el cupón por correo electrónico al socio

#### 2. Generación Masiva de Cupones Mensuales

**Acceso:**
- Tab "Generar Cupones" en la página de Facturación
- Botón "Generar Cupones" en el header

**Pantalla de Generación:**

**a) Resumen de Última Generación:**
- Tarjetas con métricas:
  - Última generación (mes/año)
  - Cupones generados (cantidad)
  - Total generado (monto)
  - Generaciones este año (cantidad)

**b) Formulario de Generación:**

**Campos Requeridos:**
1. **Mes a Generar** (Requerido):
   - Selector de mes (Enero a Diciembre)
   - Por defecto muestra el mes actual

2. **Año** (Requerido):
   - Campo numérico
   - Rango: 2020-2030
   - Por defecto muestra el año actual

3. **Fecha de Vencimiento** (Requerido):
   - Selector de fecha
   - Fecha límite para el pago de los cupones

**c) Vista Previa:**

**Funcionalidad:**
- Botón "Generar Vista Previa" para calcular antes de generar
- Muestra estadísticas:
  - Socios a procesar (cantidad)
  - Total estimado (monto)
- Tabla con detalles:
  - Socio
  - Items incluidos (ej: "Cuota mensual, Mantenimiento")
  - Monto del cupón
  - Estado (OK, Con deuda, etc.)

**d) Opciones Avanzadas:**

1. **Enviar cupones por email automáticamente** (Checkbox):
   - Si está marcado, envía los cupones por email al generar
   - Por defecto: marcado
   - Los socios recibirán su cupón en el correo registrado

**Acciones:**
- **Cancelar**: Limpia el formulario y cierra
- **Vista Previa**: Genera la vista previa sin crear los cupones
- **Generar Cupones**: Crea los cupones definitivamente (con confirmación)

**Proceso de Generación:**
1. Usuario completa el formulario
2. Opcionalmente genera vista previa
3. Hace clic en "Generar Cupones"
4. Sistema muestra confirmación
5. Se generan los cupones para todos los socios activos
6. Se incluyen automáticamente las visitas pendientes del mes
7. Se calculan los intereses si corresponde
8. Se envían por email si está configurado

#### 3. Registro de Pagos

**Modal de Registro de Pago:**

**Campos:**
- Socio (selector, requerido)
- Cupón a pagar (selector, requerido)
- Método de pago (requerido):
  - Transferencia bancaria
  - Efectivo
  - Cheque
  - Tarjeta de débito
  - Tarjeta de crédito
- Monto (requerido)
- Fecha del pago (requerido)
- Número de comprobante (opcional)
- Observaciones (opcional)

**Validaciones:**
- El monto no puede exceder el monto del cupón
- El cupón debe estar pendiente
- La fecha no puede ser futura

**Acciones:**
- **Cancelar**: Cierra sin guardar
- **Registrar Pago**: Guarda el pago y actualiza el estado del cupón

#### 4. Listado de Pagos

**Tabla de Pagos:**
- Columnas:
  - Fecha
  - Socio
  - Cupón
  - Monto
  - Método de pago
  - Estado de conciliación
  - Acciones

**Filtros:**
- Por socio
- Por método de pago
- Por estado de conciliación
- Por rango de fechas

### Flujo de Trabajo Típico

1. **Generar cupones mensuales:**
   - Usuario accede a "Generar Cupones"
   - Selecciona mes y año
   - Define fecha de vencimiento
   - Genera vista previa (opcional)
   - Revisa las opciones avanzadas
   - Genera los cupones
   - Sistema crea los cupones y envía emails si está configurado

2. **Registrar un pago:**
   - Usuario hace clic en "Registrar Pago"
   - Selecciona el socio
   - Selecciona el cupón a pagar
   - Ingresa método de pago y monto
   - Guarda el pago
   - El cupón se marca como pagado

### Acceso
- URL: `facturacion.html`
- Acceso desde el menú principal de navegación

---

## Conciliación Bancaria

### Descripción General
Sistema inteligente de conciliación bancaria automática que procesa extractos bancarios en formato de texto (.txt), identifica a los socios mediante matching multi-nivel (CUIT/CUIL, DNI, nombre, apellido), detecta pagos duplicados y permite la asignación manual de movimientos no identificados.

### Funcionalidades Implementadas

#### 1. Carga de Archivo Bancario

**Formato Soportado:**
- Archivo de texto (.txt) del extracto bancario
- Formato: Columnas separadas por tabuladores
- Encoding: ISO-8859-1 o Windows-1252 (típico de extractos bancarios argentinos)

**Columnas Procesadas:**
- Fecha del movimiento
- Sucursal de origen
- Descripción de la sucursal
- Código operativo
- Referencia bancaria
- Concepto (información clave)
- Importe en pesos
- Saldo en pesos

**Interfaz de Carga:**
- **Drag & Drop**: Arrastrar y soltar el archivo directamente
- **Selector de archivo**: Botón para seleccionar desde el explorador
- **Vista previa**: Muestra las primeras 10 líneas del archivo antes de procesar
- **Información del archivo**:
  - Nombre del archivo
  - Tamaño
  - Cuenta bancaria identificada
  - Botones de acción: "Procesar Archivo" y "Cancelar"

**Proceso de Carga:**
1. Usuario carga el archivo .txt del extracto bancario
2. Sistema muestra vista previa del contenido
3. Usuario confirma y hace clic en "Procesar Archivo"
4. Sistema inicia el procesamiento con barra de progreso

#### 2. Procesamiento y Parsing del Archivo

**Algoritmo de Parsing:**

**a) Identificación de Movimientos:**
- El sistema lee línea por línea el archivo
- Identifica y descarta líneas de encabezado (ej: "Movimientos del Día", "Fecha\tSuc. Origen", etc.)
- Parsea cada línea separando por tabuladores
- Extrae solo las "Transferencias Recibidas" (ingresos)
- Ignora débitos, comisiones, impuestos y otros movimientos de salida

**b) Extracción de Datos del Concepto:**

El sistema utiliza expresiones regulares (regex) para extraer información del campo "Concepto":

**Patrones reconocidos:**
1. `De Apellido, Nombre / observación / CUIT`
   - Ejemplo: "De Costa, Oscar Daniel / - Var / 20115274059"
2. `De Apellido/Nombre / observación / CUIT`
   - Ejemplo: "De Martinelli/veronica / - Var / 27253428630"

**Información extraída:**
- Apellido del transferente
- Nombre del transferente
- CUIT/CUIL completo (11 dígitos)
- DNI (extraído del CUIT: se quitan los primeros 2 dígitos y el último)
- Monto de la transferencia
- Fecha del movimiento
- Referencia bancaria

**Barra de Progreso:**
- 0-30%: Parseando archivo
- 30-50%: Extrayendo datos
- 50-70%: Buscando coincidencias
- 70-90%: Verificando duplicados
- 90-100%: Procesamiento completado

#### 3. Sistema de Matching Inteligente Multi-Nivel

El sistema implementa un algoritmo de matching jerárquico con diferentes niveles de confianza:

**A. Match Exacto por CUIT/CUIL (Confianza: 100%)**
- Compara el CUIT extraído del extracto con el CUIT registrado en la base de socios
- Si hay coincidencia exacta, se asigna automáticamente
- Badge: Verde "Match exacto - CUIT"
- Este es el nivel más confiable de matching

**B. Match Exacto por DNI (Confianza: 95%)**
- Extrae el DNI del CUIT (posiciones 3 a 10)
- Ejemplo: CUIT 20115274059 → DNI 11527405
- Compara con el DNI de los socios registrados
- Badge: Verde "Match exacto - DNI"
- Muy confiable, prácticamente sin falsos positivos

**C. Match Bidireccional por CUIL Generado (Confianza: 98%)**
- **NUEVA FUNCIONALIDAD**: Matching inverso cuando el socio solo tiene DNI registrado
- El sistema genera los 4 posibles CUILs a partir del DNI del socio:
  - 20-DNI-X (Hombres)
  - 27-DNI-X (Mujeres)
  - 23-DNI-X (Casos especiales)
  - 24-DNI-X (Casos especiales)
- Calcula el dígito verificador correcto usando el algoritmo oficial argentino
- Compara los CUILs generados con el CUIL del extracto bancario
- Badge: Verde "Match exacto - CUIL"
- **Ventaja**: Funciona incluso si el socio está cargado solo con DNI en la base de datos
- Muy confiable, confianza del 98% por la validación matemática del dígito verificador

**D. Match por Apellido y Nombre Completo (Confianza: 85%)**
- Normaliza el texto (quita acentos, convierte a minúsculas, elimina espacios extra)
- Busca coincidencia exacta de apellido Y nombre en los datos del socio
- Útil cuando no hay CUIT/CUIL disponible
- Badge: Azul "Match por nombre completo"
- Confiable pero puede tener algunas ambigüedades

**E. Match por Apellido Similar (Confianza: Variable 60-80%)**
- Utiliza el algoritmo de **Levenshtein Distance** para calcular similitud entre strings
- Compara el apellido del extracto con los apellidos de los socios
- Umbral de aceptación: > 80% de similitud
- Ejemplo: "Gonzalez" vs "González" = 95% similar
- Badge: Amarillo "Apellido similar (XX% coincidencia)"
- Requiere revisión manual antes de confirmar

**F. Sin Match (Confianza: 0%)**
- No se encuentra ninguna coincidencia con ningún criterio
- Badge: Rojo "Sin coincidencia"
- Requiere asignación manual por parte del usuario
- Puede ser un nuevo socio, un error o un pago que no corresponde al club

**G. No corresponde al club (Confianza: 0%)**
- Transferencias identificadas manualmente como "No es pago de socio"
- Badge: Gris "No es pago de socio"
- Ejemplos: Pagos a proveedores, devoluciones, movimientos internos

**Algoritmo de Normalización de Texto:**
```
normalizar(texto):
  1. Convertir a minúsculas
  2. Eliminar acentos (á→a, é→e, í→i, ó→o, ú→u, ñ→n)
  3. Trim espacios al inicio y final
  4. Quitar caracteres especiales
  5. Retornar texto normalizado
```

**Algoritmo de Similitud (Levenshtein Distance):**
- Calcula la "distancia de edición" entre dos strings
- Cuenta las operaciones mínimas (inserción, eliminación, sustitución) para transformar un string en otro
- Convierte la distancia en porcentaje de similitud
- Fórmula: similitud = 1 - (distancia / longitudMáxima)

#### 4. Detección de Pagos Duplicados

**Criterios de Detección:**

El sistema verifica si un pago ya fue registrado previamente comparando:

1. **Mismo socio identificado**
2. **Fecha similar** (±2 días de tolerancia)
   - Ejemplo: Pago el 10/11 puede matchear con registro del 09/11 o 11/11
3. **Monto idéntico** (diferencia < $1)
4. **Referencia bancaria** (opcional, para mayor precisión)

**Resultado de Detección:**
- Si se detecta duplicado:
  - Badge: Naranja "Ya Registrado"
  - Muestra información del registro previo (fecha, monto, referencia)
  - Se excluye de la confirmación masiva automática
  - Usuario puede ver detalles y decidir si descartar o procesar como nuevo pago

**Información del Duplicado:**
- Fecha del registro previo
- Monto del pago previo
- Referencia del pago previo
- Diferencia de días entre ambos movimientos

#### 5. Métricas y Dashboard de Resultados

**Cards de Resumen (Superior):**

1. **Total Movimientos**:
   - Cantidad total de transferencias recibidas procesadas
   - Incluye todos los estados

2. **Match Exacto**:
   - Cantidad de movimientos con match por CUIT/DNI
   - Monto total de estos movimientos
   - Color: Verde
   - Listos para confirmación automática

3. **Match Probable**:
   - Cantidad de movimientos con match por nombre o apellido similar
   - Monto total de estos movimientos
   - Color: Amarillo
   - Requieren revisión antes de confirmar

4. **Sin Coincidencia**:
   - Cantidad de movimientos sin match
   - Monto total sin asignar
   - Color: Rojo
   - Requieren asignación manual

5. **Ya Registrados**:
   - Cantidad de movimientos duplicados
   - Monto total de duplicados
   - Color: Naranja
   - Para revisión o descarte

**Actualización Automática:**
- Las métricas se actualizan en tiempo real al realizar acciones
- Los contadores en los tabs también se actualizan dinámicamente

#### 6. Tabs de Clasificación

El sistema organiza los resultados en 5 tabs para facilitar la revisión:

**Tab 1: Todos**
- Muestra todos los movimientos procesados
- Incluye columna de selección (checkbox)
- Filtros disponibles para búsqueda rápida
- Acciones disponibles:
  - Seleccionar/deseleccionar todos
  - Confirmar seleccionados
  - Exportar resultados
  - Descartar todo

**Tab 2: Match Exacto**
- Solo movimientos con match CUIT/DNI (confianza 95-100%)
- Checkbox para selección múltiple
- Acción destacada: "Confirmar Todos" (verde)
- Estos son los más seguros para confirmar en masa

**Tab 3: Match Probable**
- Movimientos con match por nombre o apellido similar (60-85%)
- Requieren revisión individual
- Checkbox para selección
- Muestra porcentaje de confianza en cada fila
- Acción: "Confirmar Seleccionados" (azul)

**Tab 4: Sin Match**
- Movimientos sin ninguna coincidencia
- NO incluye checkbox (deben asignarse manualmente)
- Selector de socio en cada fila
- Acciones:
  - "Asignar" (asignar al socio seleccionado)
  - "No es socio" (marcar como no perteneciente al club)

**Tab 5: Duplicados**
- Movimientos ya registrados previamente
- Muestra información del registro previo
- Acciones:
  - "Ver" (detalle del duplicado)
  - "Descartar" (eliminar del procesamiento)

**Tabla de Movimientos:**

**Columnas Mostradas:**
- Checkbox (excepto en tabs Sin Match y Duplicados)
- Fecha del movimiento
- Nombre/Apellido (del extracto bancario)
- CUIT/CUIL (si está disponible)
- Monto (formateado con separador de miles)
- Socio Identificado (nombre completo del socio en la base)
- Match (badge con nivel y porcentaje de confianza)
- Estado (Nuevo / Ya Registrado)
- Acciones (botones de acción específicos)

**Badges de Matching:**
- Verde brillante: "Match exacto - CUIT" (100%)
- Verde brillante: "Match exacto - CUIL" (98%) - **NUEVO**: Calculado desde DNI
- Verde agua: "Match exacto - DNI" (95%)
- Azul: "Match por nombre completo" (85%)
- Amarillo: "Apellido similar (XX%)" (60-80%)
- Rojo: "Sin coincidencia" (0%)
- Gris: "No es pago de socio" (0%)
- Naranja: "Ya Registrado" (duplicado)

#### 7. Acciones por Movimiento

**Para Movimientos con Match (Exacto o Probable):**

1. **Confirmar** (botón verde):
   - Registra el pago individualmente
   - Actualiza el estado del cupón a "Pagado"
   - Muestra confirmación al usuario
   - El movimiento desaparece de la lista de pendientes

2. **Ver Detalle** (botón azul):
   - Muestra modal con información completa:
     - Fecha y concepto del extracto
     - Monto y referencia bancaria
     - Datos extraídos (apellido, nombre, CUIT, DNI)
     - Socio identificado (nombre, DNI, CUIT)
     - Nivel de match y confianza
     - Información de duplicado (si aplica)

3. **Cambiar Socio** (botón amarillo):
   - Permite reasignar manualmente el movimiento a otro socio
   - Útil cuando el matching automático se equivocó
   - Abre selector de socios
   - Al confirmar, actualiza la asignación con confianza 100%

**Para Movimientos Sin Match:**

1. **Selector de Socio** (dropdown):
   - Lista de todos los socios activos
   - Muestra: Nombre completo - DNI
   - Permite búsqueda/filtrado

2. **Asignar** (botón verde):
   - Asigna el movimiento al socio seleccionado
   - Marca como "Asignación manual" con confianza 100%
   - El movimiento pasa a "Match Exacto"

3. **No es socio** (botón gris):
   - Marca el movimiento como "No es pago de socio"
   - Lo excluye de futuros procesamientos
   - Útil para pagos de proveedores, devoluciones, etc.

**Para Movimientos Duplicados:**

1. **Ver** (botón azul):
   - Muestra detalles del movimiento y del registro previo
   - Comparación de fechas y montos
   - Permite verificar si realmente es un duplicado

2. **Descartar** (botón rojo):
   - Elimina el movimiento del procesamiento actual
   - Confirmación requerida
   - No afecta el registro previo

#### 8. Confirmación de Pagos

**Confirmación Masiva de Matches Exactos:**

**Acceso:**
- Botón "Confirmar Todos los Exactos" (verde, en todos los tabs excepto Duplicados)
- Tab "Match Exacto" → Botón "Confirmar Todos"

**Proceso:**
1. Sistema filtra todos los movimientos con:
   - Match exacto por CUIT/DNI (confianza 95-100%)
   - Estado "Nuevo" (no duplicados)
   - Socio identificado válido
2. Muestra modal de confirmación con:
   - Total de pagos a confirmar
   - Monto total a registrar
   - Lista resumen de movimientos
3. Usuario confirma la acción
4. Sistema registra todos los pagos simultáneamente:
   - Crea registro de pago por cada movimiento
   - Actualiza estado de cupones a "Pagado"
   - Registra fecha, hora y método (Transferencia bancaria)
   - Guarda referencia bancaria
5. Muestra resultado de la operación:
   - Cantidad de pagos registrados exitosamente
   - Monto total procesado
   - Log de la operación con timestamp

**Confirmación de Seleccionados:**

**Acceso:**
- Botón "Confirmar Seleccionados" (azul)
- Disponible en tabs "Todos", "Match Exacto" y "Match Probable"

**Proceso:**
1. Usuario marca checkboxes de los movimientos deseados
2. Hace clic en "Confirmar Seleccionados"
3. Sistema valida:
   - Que haya al menos un movimiento seleccionado
   - Que los movimientos no sean duplicados
   - Que tengan socio asignado
4. Muestra modal de confirmación similar al masivo
5. Registra solo los pagos seleccionados
6. Actualiza la interfaz y métricas

**Validaciones:**
- No se pueden confirmar movimientos sin socio asignado
- No se pueden confirmar duplicados
- Se requiere confirmación explícita del usuario
- Cada confirmación genera un log de auditoría

#### 9. Funciones Auxiliares

**Exportar Resultados:**
- Botón "Exportar Resultados" (amarillo)
- Genera archivo descargable con:
  - Todos los movimientos procesados
  - Estado de matching de cada uno
  - Socios asignados
  - Montos y fechas
  - Estadísticas del procesamiento
- Formatos disponibles: Excel (.xlsx) o PDF

**Descartar Todo:**
- Botón "Descartar Todo" (rojo)
- Requiere confirmación
- Elimina todo el procesamiento actual
- Vuelve a la pantalla de carga inicial
- No afecta datos previamente guardados

**Búsqueda y Filtrado:**
- Campo de búsqueda rápida por:
  - Nombre/Apellido
  - CUIT/DNI
  - Monto
  - Fecha
- Filtros en tiempo real
- Mantiene la clasificación por tabs

### Flujo de Trabajo Completo

**1. Obtener Extracto Bancario:**
- Usuario descarga el extracto del banco en formato .txt
- Verifica que sea el formato correcto (columnas tabuladas)

**2. Cargar Archivo:**
- Accede a "Conciliación Bancaria"
- Arrastra el archivo o usa el selector
- Revisa la vista previa
- Confirma y procesa

**3. Revisión de Resultados:**
- Sistema muestra métricas generales
- Usuario revisa cada tab según prioridad:
  1. **Match Exacto**: Confirmar todos o revisar individualmente
  2. **Match Probable**: Revisar y confirmar los correctos
  3. **Sin Match**: Asignar manualmente
  4. **Duplicados**: Verificar y descartar

**4. Confirmación:**
- Confirma matches exactos en masa (más rápido)
- Revisa y confirma probables individualmente
- Asigna manualmente los sin match
- Descarta duplicados

**5. Verificación:**
- Revisa el resumen de pagos confirmados
- Exporta reporte si necesita
- Verifica que los cupones se hayan actualizado a "Pagado"

**6. Registro y Auditoría:**
- Sistema genera log de la conciliación:
  - Fecha y hora del procesamiento
  - Usuario que realizó la operación
  - Cantidad de movimientos procesados
  - Cantidad de pagos confirmados
  - Monto total conciliado
  - Movimientos descartados o sin asignar

### Ventajas de este Sistema

**Para el Usuario:**
- **Ahorro de tiempo**: Procesa cientos de movimientos en minutos
- **Precisión**: Matching automático reduce errores humanos
- **Flexibilidad**: Permite revisión y corrección manual cuando es necesario
- **Transparencia**: Muestra claramente el nivel de confianza de cada match
- **Control**: El usuario siempre tiene la última palabra en las confirmaciones

**Para el Club:**
- **Eficiencia operativa**: Reduce horas de trabajo manual
- **Menor tasa de error**: Automatización de tareas repetitivas
- **Mejor seguimiento**: Logs de auditoría completos
- **Visibilidad**: Métricas en tiempo real del estado de cobros
- **Escalabilidad**: Puede procesar extractos de cualquier tamaño

### Casos de Uso Comunes

**Caso 1: Conciliación Mensual Estándar**
- Escenario: Fin de mes, 150 socios han pagado
- Proceso:
  1. Descarga extracto del banco (300 movimientos)
  2. Sistema procesa en 30 segundos
  3. Identifica 140 matches exactos (93%)
  4. Confirma los 140 en un solo clic
  5. Revisa manualmente 10 probables y confirma
  6. Total de tiempo: 5-10 minutos

**Caso 2: Transferencia sin CUIT**
- Escenario: Socio transfiere sin poner su CUIT en el concepto
- Sistema busca por nombre y apellido
- Encuentra match con 85% de confianza
- Usuario revisa, confirma manualmente
- Pago registrado correctamente

**Caso 3: Socio Nuevo o Visitante**
- Escenario: Transferencia de persona no registrada
- Sistema marca como "Sin match"
- Usuario verifica si es socio nuevo o visitante
- Opción 1: Asigna a socio existente si lo identifica
- Opción 2: Marca como "No es socio" y gestiona aparte

**Caso 4: Pago Duplicado Real**
- Escenario: Socio transfiere dos veces por error
- Sistema detecta el duplicado
- Muestra ambos movimientos
- Usuario verifica con el socio
- Confirma uno y descarta el otro (o gestiona devolución)

### Consideraciones Técnicas

**Rendimiento:**
- Procesa hasta 500 movimientos en menos de 1 minuto
- Utiliza procesamiento local (JavaScript en el navegador)
- No requiere servidor pesado para el matching
- Eficiente incluso con bases de datos de miles de socios

**Seguridad:**
- Los archivos se procesan localmente
- No se suben archivos sensibles a servidores externos
- Logs de auditoría para trazabilidad
- Validaciones en cada paso crítico

**Mantenibilidad:**
- Algoritmos de matching fácilmente ajustables
- Umbrales de confianza configurables
- Patrones regex extensibles para nuevos formatos
- Código modular y bien documentado

### Acceso
- URL: `conciliacion.html`
- Acceso desde el menú principal de navegación
- Requiere permisos de administrador o tesorero

---

## Portal de Autogestión para Socios

### Descripción General
Portal web para que los socios del club puedan consultar su estado de cuenta de manera autónoma, ver cupones pendientes, historial de pagos y acceder a los datos bancarios necesarios para realizar pagos. Reduce significativamente las consultas administrativas repetitivas.

### Funcionalidades Implementadas

#### 1. Sistema de Autenticación

**Método de Acceso:**
- **DNI** (sin puntos ni guiones): Campo numérico de 8 dígitos
- **Número de Socio**: Identificador único del socio en el sistema
- Validación en tiempo real
- Mensajes de error claros y seguros

**Seguridad:**
- Mensajes de error genéricos para no revelar información sensible
- Validación de formato de DNI
- Rate limiting visual (contador de intentos)
- Sesión que se cierra al salir

**Interfaz de Login:**
- Diseño limpio y profesional
- Logo del club prominente
- Formulario centrado y fácil de usar
- Links de ayuda:
  - "¿Olvidaste tu número de socio?"
  - "Contacto" para problemas de acceso
- **Sección de Ejemplos para Pruebas:**
  - 4 ejemplos de socios con diferentes estados
  - Ejemplos clickeables que llenan automáticamente el formulario
  - Badges de estado visuales (Al día, Por vencer, Con deuda)
  - Facilita las pruebas del sistema sin necesidad de recordar credenciales
  - Ejemplos disponibles:
    - Oscar Daniel Costa (DNI: 11527405, Socio: 001) - Al día
    - María Isabel Pérez Gilligan (DNI: 14611735, Socio: 002) - Cupón por vencer
    - Carlos Daniel Santini (DNI: 20439648, Socio: 003) - Con deuda vencida
    - Juan José Cravarezza (DNI: 6591470, Socio: 004) - Al día
- Responsive y mobile-friendly

#### 2. Dashboard del Socio

**Header del Socio:**
- Nombre completo del socio
- Número de socio
- DNI (parcialmente oculto por seguridad)
- Estado: Activo/Inactivo (badge visual)
- Botón "Cerrar Sesión"

**Cards de Resumen (3 cards principales):**

**Card 1: Deuda Actual**
- Monto total adeudado (destacado en grande)
- Cantidad de cupones pendientes
- Color de borde:
  - Rojo: Si hay deuda
  - Verde: Si está al día
- Icono de alerta si hay cupones vencidos

**Card 2: Último Pago**
- Fecha del último pago registrado
- Monto del último pago
- Mensaje "Sin pagos registrados" si no hay historial
- Color verde (éxito)

**Card 3: Próximo Vencimiento**
- Fecha del próximo cupón que vence
- Monto del cupón
- Color amarillo (advertencia)
- Mensaje "Sin cupones pendientes" si está al día

#### 3. Cupones Pendientes

**Tabla Completa con:**
- Número de cupón
- Período (Mes/Año)
- Fecha de emisión
- Fecha de vencimiento
- Monto original
- Intereses (si aplica)
- **Total a pagar** (monto + intereses)
- Estado con badge de color
- Botón "Ver" para detalle completo

**Estados Visuales:**
- **Badge Verde "Pendiente"**: Cupón dentro del plazo de pago
- **Badge Amarillo "Por vencer"**: Cupón próximo a vencer (menos de 5 días)
- **Badge Rojo "Vencido"**: Cupón vencido con días de mora indicados

**Totales al Pie:**
- Subtotal de cupones (sin intereses)
- Total de intereses por mora
- **TOTAL A PAGAR** (destacado en rojo y grande)

**Estado Vacío:**
- Mensaje: "¡Estás al día! No tienes cupones pendientes."
- Icono de check verde
- Diseño amigable

#### 4. Modal de Detalle de Cupón

**Información del Cupón:**
- Número completo del cupón
- Período facturado
- Fecha de emisión
- Fecha de vencimiento
- Días de mora (si aplica, destacado en rojo)

**Desglose de Items:**
Tabla detallada con:
- Descripción del item (Cuota mensual, Visitas, Mantenimiento, etc.)
- Cantidad
- Precio unitario
- Subtotal por item

**Cálculo de Totales:**
- Subtotal del cupón (suma de items)
- Intereses por mora (si aplica)
- **TOTAL A PAGAR** (destacado)

**Diseño:**
- Modal centrado y responsive
- Botón de cierre (X)
- Scroll interno si el contenido es extenso
- Formato claro y fácil de leer

#### 5. Historial de Pagos

**Tabla de Pagos Realizados:**

Columnas:
- Fecha de pago
- Cupón pagado (número)
- Período del cupón
- Método de pago (Transferencia, Efectivo, Cheque)
- Monto pagado
- Estado de conciliación (badge verde "Conciliado")

**Filtros Disponibles:**
- **Por Año**: Dropdown con años disponibles automáticamente
- **Por Método**: Transferencia, Efectivo, Cheque, Todos
- Filtros aplicables en tiempo real
- Se mantienen al cambiar entre filtros

**Estado Vacío:**
- Mensaje cuando no hay pagos con los filtros seleccionados
- Icono de historial
- Diseño consistente

**Ordenamiento:**
- Por defecto: Más recientes primero
- Muestra últimos 12 meses por defecto
- Preparado para paginación si el historial es extenso

#### 6. Datos para Pago

**Sección Simplificada con:**

**Datos Bancarios:**
- Banco: Santander Río
- CBU: Número completo con botón "Copiar"
- Código de Referencia: Código único del socio (ej: NCNE001)
  - Formato: NCNE + número de socio (3 dígitos)
  - Destacado visualmente (fondo amarillo, texto grande)
  - Botón "Copiar" para facilitar uso

**Funcionalidad de Copiar:**
- Botones "Copiar" junto a CBU y código de referencia
- Notificación al copiar exitosamente
- Fallback para navegadores antiguos
- Facilita el proceso de pago

**Diseño:**
- Fondo azul claro (e3f2fd)
- Tarjeta blanca con datos
- Items bien espaciados
- Fácil de leer y usar

#### 7. Alertas y Notificaciones

**Banner de Alerta Superior:**

**Si está al día:**
- Fondo verde
- Mensaje: "¡Estás al día! No tienes cupones pendientes."
- Icono de check

**Si hay cupones vencidos:**
- Fondo rojo
- Mensaje: "Tienes X cupones vencidos por un total de $X. Por favor realiza el pago lo antes posible."
- Icono de alerta
- Muy visible y destacado

**Si hay cupones por vencer:**
- Banner no se muestra (o se puede configurar para mostrar advertencia amarilla)

#### 8. Características Adicionales

**Responsive Design:**
- Funciona perfectamente en móviles
- Tablas con scroll horizontal en pantallas pequeñas
- Cards apiladas verticalmente en móvil
- Formularios adaptados

**Accesibilidad:**
- Colores con buen contraste
- Tamaños de fuente legibles
- Iconos descriptivos
- Navegación clara

**UX Optimizada:**
- Carga rápida
- Transiciones suaves
- Feedback visual en todas las acciones
- Mensajes claros y útiles

### Flujo de Usuario Típico

**1. Acceso:**
- Socio accede a `mi-cuenta.html`
- Ve pantalla de login con logo del club

**2. Autenticación:**
- Ingresa DNI (ej: 11527405)
- Ingresa número de socio (ej: 001)
- Hace clic en "Consultar mi Cuenta"
- Sistema valida y carga datos

**3. Visualización del Dashboard:**
- Ve su nombre y estado en el header
- Revisa las 3 cards de resumen:
  - Deuda actual (si tiene)
  - Último pago realizado
  - Próximo vencimiento

**4. Revisión de Cupones:**
- Ve tabla de cupones pendientes
- Identifica cuáles están vencidos (badge rojo)
- Ve el total a pagar destacado
- Hace clic en "Ver" para ver detalle de un cupón específico

**5. Consulta de Historial:**
- Revisa pagos realizados
- Filtra por año o método si necesita
- Verifica que sus pagos estén registrados

**6. Obtención de Datos para Pago:**
- Ve CBU del club
- Ve su código de referencia único
- Copia ambos datos fácilmente
- Realiza transferencia en su banco

**7. Cierre de Sesión:**
- Hace clic en "Cerrar Sesión"
- Vuelve a la pantalla de login

### Beneficios

**Para los Socios:**
- ✅ **Consulta 24/7**: Acceso en cualquier momento sin depender del horario del club
- ✅ **Información clara**: Ve exactamente cuánto debe y cuándo vence
- ✅ **Facilidad de pago**: Datos bancarios y código de referencia siempre disponibles
- ✅ **Transparencia total**: Historial completo de pagos y movimientos
- ✅ **Autonomía**: No necesita llamar o ir al club para consultas básicas

**Para el Club:**
- ✅ **Reduce consultas**: Menos llamadas y visitas por consultas de estado de cuenta
- ✅ **Mejora experiencia**: Imagen moderna y profesional
- ✅ **Aumenta pagos a tiempo**: Los socios ven claramente sus vencimientos
- ✅ **Eficiencia operativa**: El personal se enfoca en tareas más importantes
- ✅ **Comunicación proactiva**: Los socios están mejor informados

### Casos de Uso

**Caso 1: Socio al día**
- Accede al portal
- Ve mensaje "¡Estás al día!"
- Revisa su historial de pagos
- Confirma que todo está correcto
- Tiempo: 2 minutos

**Caso 2: Socio con cupón por vencer**
- Accede al portal
- Ve alerta amarilla en cupón
- Ve que vence en 3 días
- Copia CBU y código de referencia
- Realiza transferencia
- Tiempo: 5 minutos

**Caso 3: Socio con deuda vencida**
- Accede al portal
- Ve banner rojo de alerta
- Ve cupones vencidos con días de mora
- Ve total con intereses
- Revisa detalle de cada cupón
- Realiza pago del total
- Tiempo: 10 minutos

**Caso 4: Socio consultando historial**
- Accede al portal
- Va a sección "Historial de Pagos"
- Filtra por año 2025
- Verifica todos sus pagos
- Exporta o toma captura si necesita
- Tiempo: 3 minutos

### Consideraciones Técnicas

**Seguridad:**
- Autenticación simple pero efectiva (DNI + Nro. Socio)
- No se muestra información sensible completa
- Sesión que se cierra al salir
- Validaciones en frontend y backend (en producción)

**Performance:**
- Carga rápida de datos
- Renderizado eficiente de tablas
- Sin dependencias pesadas
- Optimizado para móviles

**Mantenibilidad:**
- Código modular y bien estructurado
- Fácil de extender con nuevas funcionalidades
- Datos de ejemplo realistas para testing

### Acceso
- URL: `mi-cuenta.html`
- Acceso público (no requiere permisos especiales)
- Disponible desde el menú principal en `index.html`
- Link directo para compartir con socios

---

## Configuración del Sistema

### Descripción General
Módulo centralizado para gestionar los parámetros configurables del sistema. Permite modificar costos, datos bancarios e información del club sin necesidad de editar código. Los valores configurados se almacenan localmente y son utilizados por todos los módulos del sistema.

### Funcionalidades Implementadas

#### 1. Información del Club
Gestión de datos básicos de la organización:
- **Nombre del club** (obligatorio)
- **Dirección completa**: Ubicación física del club
- **Teléfonos**: Principal y secundario para contacto
- **Emails de contacto**: Principal (obligatorio) y secundario
- **Sitio web**: URL del sitio web del club (opcional)

**Uso:** Estos datos se utilizan en facturas, cupones, emails y el portal de socios.

#### 2. Datos Bancarios
Configuración de información bancaria para recepción de pagos:
- **CBU** (obligatorio): Clave Bancaria Uniforme de 22 dígitos
- **Alias CBU**: Alias opcional para facilitar transferencias
- **Banco**: Nombre de la entidad bancaria
- **Titular de la cuenta** (obligatorio): Nombre del titular
- **Tipo de cuenta**: Caja de Ahorro (CA) o Cuenta Corriente (CC)

**Validaciones:**
- El CBU debe tener exactamente 22 dígitos
- Formato automático al ingresar

**Integración:** El CBU configurado se muestra automáticamente en el Portal de Autogestión para que los socios realicen pagos.

#### 3. Costos y Tarifas
Gestión de precios y valores de servicios:

**Visitas:**
- **Costo por visita** (obligatorio): Monto que se cobra por cada persona visitante
- Valor predeterminado: $5,000
- Se aplica automáticamente al generar cupones con visitas

**Cuotas:**
- **Cuota mensual base**: Monto base de la cuota social mensual
- Valor predeterminado: $45,000

**Amarras (por tamaño de embarcación):**
- **Amarra chica**: Hasta 6 metros (predeterminado: $15,000)
- **Amarra mediana**: 6 a 10 metros (predeterminado: $25,000)
- **Amarra grande**: Más de 10 metros (predeterminado: $35,000)

**Integración:** El costo de visita configurado se usa automáticamente en el módulo de Gestión de Socios al cargar visitas.

#### 4. Facturación
Parámetros del sistema de facturación y generación de cupones:

- **Día de vencimiento** (obligatorio): Día del mes en que vencen los cupones (ej: 15)
- **Días de gracia**: Cantidad de días antes de aplicar intereses por mora
  - Valor predeterminado: 5 días
  - Rango: 0-30 días
- **Tasa de interés por mora (%)**: Porcentaje mensual de interés sobre saldo vencido
  - Valor predeterminado: 3%
  - Permite decimales (ej: 3.5, 2.75)
- **Generación automática**: Checkbox para generar cupones automáticamente cada mes
  - Activado por defecto

#### 5. Navegación y Organización
La configuración está organizada en tabs laterales para fácil acceso:

**Categorías:**
1. Información del Club 🏢
2. Datos Bancarios 🏦
3. Costos y Tarifas 💲
4. Facturación 📄

**Interfaz:**
- Menú lateral con navegación clara entre secciones
- Campos agrupados lógicamente por subsecciones
- Mensajes de ayuda debajo de campos importantes
- Indicadores visuales de campos obligatorios (*)

#### 6. Acciones Disponibles
Botones de acción en cada sección:

**Guardar Cambios:**
- Persiste la configuración en `localStorage`
- Valida campos obligatorios antes de guardar
- Muestra mensaje de confirmación

**Cancelar:**
- Descarta cambios y recarga valores guardados
- No requiere confirmación

**Restaurar Predeterminados:**
- Vuelve a los valores iniciales del sistema
- Requiere confirmación (acción irreversible)
- Útil para resetear después de pruebas
- Disponible en la sección de Facturación

### Persistencia de Datos

**Almacenamiento:**
- Todos los valores se guardan en `localStorage` del navegador
- Clave: `clubConfig`
- Formato: JSON estructurado por categorías

**Estructura de Datos:**
```javascript
{
  club: {
    nombre, direccion, telefono1, telefono2,
    email1, email2, web
  },
  bancario: {
    cbu, alias, banco, titular, tipoCuenta
  },
  costos: {
    visita, cuotaMensual, 
    amarraChica, amarraMediana, amarraGrande
  },
  facturacion: {
    diaVencimiento, diasGracia, 
    tasaInteres, generacionAuto
  }
}
```

**Acceso desde Otros Módulos:**
Los otros módulos acceden a la configuración mediante la función global `getConfig()`:
```javascript
const config = getConfig();
const costoVisita = config.costos.visita;
const cbu = config.bancario.cbu;
```

### Validaciones Implementadas

1. **Campos Obligatorios:**
   - Nombre del club
   - Email de contacto
   - CBU
   - Titular de cuenta bancaria
   - Costo por visita
   - Día de vencimiento

2. **Formato de Datos:**
   - CBU: Exactamente 22 dígitos numéricos
   - Email: Formato de email válido
   - Números: Solo valores positivos para costos
   - Porcentajes: Entre 0 y 100

3. **Rangos:**
   - Día de vencimiento: Entre 1 y 31
   - Días de gracia: Entre 0 y 30
   - Tasa de interés: Entre 0 y 100

### Acceso

- **URL**: `configuracion.html`
- **Desde Dashboard**: Botón "Configuración" en acciones rápidas y en el header
- **Desde Index**: Card de "Configuración del Sistema"
- **Desde otras páginas**: Link "Configuración" en el header de todas las páginas administrativas

### Integración con Otros Módulos

1. **Gestión de Socios** (`socios.html`):
   - Usa `config.costos.visita` para calcular el costo de visitas
   - Se actualiza automáticamente al cambiar el valor

2. **Portal de Autogestión** (`mi-cuenta.html`):
   - Muestra `config.bancario.cbu` en datos de pago
   - Se actualiza dinámicamente en cada carga

3. **Sistema de Facturación** (`facturacion.html`):
   - Aplica `config.facturacion.diaVencimiento` a cupones generados
   - Calcula intereses según `config.facturacion.tasaInteres`
   - Respeta `config.facturacion.diasGracia`

### Casos de Uso

**Caso 1: Actualizar Costo de Visitas**
1. Acceder a Configuración
2. Navegar a "Costos y Tarifas"
3. Modificar "Costo por Visita"
4. Guardar cambios
5. El nuevo costo se aplica automáticamente en Gestión de Socios

**Caso 2: Cambiar Datos Bancarios**
1. Acceder a Configuración
2. Navegar a "Datos Bancarios"
3. Actualizar CBU y/o alias
4. Guardar cambios
5. El nuevo CBU aparece en el Portal de Socios inmediatamente

**Caso 3: Modificar Parámetros de Facturación**
1. Acceder a Configuración
2. Navegar a "Facturación"
3. Ajustar día de vencimiento, días de gracia o tasa de interés
4. Guardar cambios
5. Los nuevos valores se aplican a los próximos cupones generados

---

## Notas Técnicas

### Estados y Flujos

**Estados de Cupones:**
- **Pendiente**: Cupón generado, sin pago
- **Pagado**: Cupón con pago registrado
- **Vencido**: Cupón con fecha de vencimiento pasada y sin pago

**Estados de Visitas:**
- **Pendiente**: Visita cargada, sin cupón generado (se puede editar/eliminar)
- **Con cupón generado**: Visita incluida en un cupón (no se puede editar/eliminar)

**Estados de Socios:**
- **Activo**: Socio con membresía vigente
- **Inactivo**: Socio sin membresía activa
- **Pendiente**: Socio en proceso de alta

### Validaciones Importantes

1. **Visitas:**
   - No se pueden editar/eliminar si tienen cupón generado
   - El costo por visita es fijo y configurado
   - La cantidad debe ser mayor a 0

2. **Cupones:**
   - No se pueden generar cupones duplicados para el mismo mes/año
   - Los cupones incluyen automáticamente las visitas pendientes

3. **Pagos:**
   - El monto no puede exceder el monto del cupón
   - Solo se pueden registrar pagos para cupones pendientes

### Integraciones

**Entre Módulos:**
- Las visitas se integran automáticamente en los cupones mensuales
- Los pagos se registran contra cupones específicos
- La conciliación bancaria actualiza el estado de los pagos

---

## Actualizaciones del Documento

Este documento debe actualizarse cada vez que se agreguen, modifiquen o eliminen funcionalidades del sistema. 

**Historial de Cambios:**

```
[2025-11-19] Implementación del Módulo de Configuración del Sistema
- Módulo: Configuración (configuracion.html)
- Nueva funcionalidad: Panel centralizado para gestionar parámetros del sistema
- Secciones implementadas:
  * Información del Club (nombre, dirección, contactos)
  * Datos Bancarios (CBU, alias, banco, titular)
  * Costos y Tarifas (visitas, cuotas, amarras)
  * Facturación (día vencimiento, días gracia, tasa interés)
- Persistencia: localStorage con estructura JSON
- Validaciones: Campos obligatorios, formato CBU (22 dígitos), rangos numéricos
- Acciones: Guardar, Cancelar, Restaurar Predeterminados
- Integración: socios.html usa config.costos.visita dinámicamente
- Integración: mi-cuenta.html usa config.bancario.cbu dinámicamente
- Acceso: Botón en dashboard.html, card en index.html, y links en headers
- Beneficio: Configuración centralizada sin editar código
- UX: Navegación por tabs lateral, mensajes de ayuda, alertas de confirmación

[2025-11-19] Simplificación del Dashboard y optimización de la interfaz
- Módulo: Dashboard (dashboard.html)
- Removido: Card de "Pagos Pendientes" para simplificar métricas principales
- Removido: Sección completa de "Actividad Reciente"
- Optimización: Dashboard ahora muestra solo 3 cards principales (Socios Activos, Ingresos del Mes, Embarcaciones)
- Mejora: Gráfico de ingresos ahora ocupa todo el ancho disponible
- Actualizado: Botón de acciones rápidas ahora incluye "Portal de Socios" en lugar de "Instrucciones de Pago"
- Beneficio: Interfaz más limpia y enfocada en métricas clave
- Acceso más directo al Portal de Autogestión desde el dashboard

[2025-11-19] Simplificación de acciones en cupones y generación
- Módulo: Sistema de Facturación (facturacion.html)
- Simplificado: Acciones de cupones ahora solo incluyen "Ver" y "Enviar por Email"
- Removido: Botones de impresión y registro de pago directo desde tabla de cupones
- Removido: Opción "Calcular intereses por mora" de la generación masiva de cupones
- Optimización: Opciones avanzadas ahora solo incluyen envío automático por email
- Beneficio: Interfaz más simple y enfocada en las acciones más utilizadas
- Mejora UX: Menos botones y opciones reducen la complejidad visual

[2025-11-19] Eliminación completa de instrucciones-pago.html
- Archivo eliminado: instrucciones-pago.html
- Migración: Toda la funcionalidad integrada en mi-cuenta.html (Portal de Autogestión)
- Actualizado: dashboard.html ahora apunta a Portal de Socios
- Actualizado: README.md con referencias actualizadas
- Actualizado: FUNCIONALIDADES.md sin referencias a instrucciones-pago
- Beneficio: Consolidación de funcionalidades en un solo portal
- Mejor experiencia: Socios acceden a todo desde un único punto de entrada

[2025-11-19] Auto-submit en ejemplos de login del Portal de Autogestión
- Módulo: Portal de Autogestión (mi-cuenta.html)
- Mejora: Al hacer clic en un ejemplo de login, se completan los campos y se envía automáticamente
- Delay: 300ms para que el usuario vea los campos llenándose
- Beneficio: Pruebas aún más rápidas del sistema
- UX mejorada: Un solo clic para acceder a cualquier cuenta de ejemplo

[2025-11-19] Mejoras en Portal de Autogestión
- Módulo: Portal de Autogestión (mi-cuenta.html)
- Agregado: Sección de ejemplos de login con 4 socios de prueba
- Ejemplos clickeables que llenan automáticamente el formulario
- Badges de estado en cada ejemplo (Al día, Por vencer, Con deuda)
- Mejora UX: Facilita las pruebas del sistema para usuarios y desarrolladores
- Actualizado index.html: Removida sección de Instrucciones de Pago
- Portal de Autogestión ahora es la única interfaz pública para socios

[2025-11-19] Implementado Portal de Autogestión para Socios
- Módulo: Portal de Autogestión (mi-cuenta.html)
- Nueva funcionalidad completa: Sistema de consulta de estado de cuenta para socios
- Autenticación: Por DNI + Número de Socio
- Dashboard con 3 cards de resumen: Deuda Actual, Último Pago, Próximo Vencimiento
- Tabla de cupones pendientes con estados visuales (Pendiente, Por vencer, Vencido)
- Modal de detalle de cupón con desglose completo de items e intereses
- Historial de pagos con filtros por año y método de pago
- Sección de datos bancarios con CBU y código de referencia único
- Funcionalidad de copiar al portapapeles para CBU y código
- Alertas visuales según estado (al día, vencidos, por vencer)
- Diseño responsive y mobile-friendly
- Datos de ejemplo para diferentes estados de socios (4 socios con diferentes escenarios)
- Beneficios: Reduce consultas administrativas, mejora experiencia del socio, aumenta pagos a tiempo
- Acceso: Público desde mi-cuenta.html, link destacado en index.html
- Reemplaza: La funcionalidad de Instrucciones de Pago ahora está integrada en el portal

[2025-11-19] Mejorado matching bidireccional por CUIL generado
- Módulo: Conciliación Bancaria
- Mejora: Agregado nuevo nivel de matching "C. Match Bidireccional por CUIL Generado" (98% confianza)
- Funcionalidad: El sistema ahora genera los 4 posibles CUILs a partir del DNI del socio
- Algoritmo: Implementado cálculo del dígito verificador según estándar argentino
- Tipos de CUIL generados: 20 (Hombres), 27 (Mujeres), 23 y 24 (Casos especiales)
- Ventaja: Permite matching cuando el socio solo tiene DNI registrado en la base de datos
- Mejora significativa: Aumenta la tasa de matching automático exitoso
- Badge: Verde "Match exacto - CUIL" con 98% de confianza
- Impacto: Reduce aún más los casos de "Sin match" que requieren asignación manual

[2025-11-19] Implementado sistema de conciliación bancaria automática inteligente
- Módulo: Conciliación Bancaria
- Nueva funcionalidad completa: Sistema de matching automático multi-nivel
- Parser de archivos .txt de extractos bancarios con formato de columnas tabuladas
- Extracción automática de datos mediante regex (apellido, nombre, CUIT/DNI)
- Algoritmo de matching jerárquico:
  * Match exacto por CUIT (100% confianza)
  * Match exacto por DNI (95% confianza)
  * Match por nombre completo (85% confianza)
  * Match por apellido similar usando Levenshtein Distance (60-80% confianza)
  * Sin match (requiere asignación manual)
- Detección automática de pagos duplicados con criterios de fecha, monto y referencia
- Dashboard con métricas en tiempo real (total, exactos, probables, sin match, duplicados)
- 5 tabs de clasificación para facilitar revisión (Todos, Match Exacto, Probable, Sin Match, Duplicados)
- Confirmación masiva de matches exactos y confirmación selectiva
- Asignación manual para movimientos sin match
- Funciones de exportación de resultados y auditoría
- Interfaz drag & drop con vista previa del archivo
- Barra de progreso con indicadores de cada etapa del procesamiento
- Badges de colores según nivel de matching y confianza
- Manejo de casos especiales: duplicados, sin match, no es socio
- Mejora significativa: Reduce tiempo de conciliación manual de horas a minutos

[2025-11-19] Modificado flujo de carga de visitas
- Módulo: Gestión de Socios - Carga de Visitas
- Cambio: Removido botón "Cargar Visita" del header
- Agregado: Botón "Cargar Visita" en las acciones de cada socio en la tabla
- Nuevo comportamiento: Al hacer clic en el botón de un socio, el modal se abre con ese socio ya pre-seleccionado y bloqueado
- Mejora de UX: Más intuitivo y reduce pasos para cargar una visita

[2025-10-15] Agregada funcionalidad de carga de visitas
- Módulo: Gestión de Socios
- Nueva funcionalidad: Modal de carga de visitas con cálculo automático
- Cambios técnicos: Nuevas funciones JavaScript para gestión de visitas
```

---

## Contacto y Soporte

Para consultas sobre funcionalidades o reportar problemas, contactar al equipo de desarrollo.

---

**Fin del Documento**

