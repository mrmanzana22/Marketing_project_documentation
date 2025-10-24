# 📚 SISTEMA DE GESTIÓN Y SINCRONIZACIÓN DE CONTENIDO MARKETING

## 🎯 Objetivo del Sistema

Este sistema automatiza la gestión de contenido de marketing para Mr. Manzana, sincronizando automáticamente la información desde Notion hacia GitHub, manteniendo una documentación actualizada en tiempo real.

---

## 🏗️ Arquitectura del Sistema

```
┌─────────────────────────────────────────────────────────┐
│                      NOTION                             │
│  ┌─────────────┐ ┌──────────────┐ ┌──────────────┐    │
│  │ Plan del    │ │ Guía de      │ │ Base Datos   │    │
│  │ Mes         │ │ Producción   │ │ Anuncios     │    │
│  └─────────────┘ └──────────────┘ └──────────────┘    │
└──────────┬──────────────┬───────────────┬──────────────┘
           │              │               │
           │ (Sincronización automática cada minuto)
           │              │               │
           └──────────────┼───────────────┘
                          ▼
           ┌──────────────────────────────┐
           │   N8N - WORKFLOW UNIFICADO   │
           │  ┌────────┐  ┌────────┐     │
           │  │ Flujo  │  │ Flujo  │     │
           │  │ Plan   │  │ Guía   │ ... │
           │  └────────┘  └────────┘     │
           │   (Ejecución en paralelo)   │
           └──────────────┬───────────────┘
                          │
                          │ (Generación de archivos Markdown)
                          │
                          ▼
           ┌──────────────────────────────┐
           │          GITHUB               │
           │    ┌─────────────────────┐   │
           │    │ 01-documentacion/   │   │
           │    │  - plan-del-mes.md  │   │
           │    │  - guia-produccion  │   │
           │    │  - base-datos...    │   │
           │    └─────────────────────┘   │
           └──────────────┬───────────────┘
                          │
                          │ (Notificaciones de cambios)
                          │
                          ▼
           ┌──────────────────────────────┐
           │         WHATSAPP             │
           │    (Alertas automáticas)     │
           └──────────────────────────────┘
```

---

## 📊 Las 3 Bases de Datos en Notion

### 1. 📅 Plan del Mes

**Propósito:** Organizar y planificar todo el contenido que se producirá durante el mes

**Campos principales:**
- **Nombre:** Título del contenido
- **Línea:** Ventas o Servicio Técnico
- **Fase:** Presentación, Evaluación o Conversión
- **Formato:** Video, Imagen, Carrusel o Slideshow
- **Estado:** Por Hacer, En Preparación, Listo para Producir, Producido o Publicado
- **Prioridad:** 🔴 Alta, 🟡 Media, 🟢 Baja
- **Producto/Servicio:** iPhone específico o servicio técnico
- **Día de Grabación:** Día Ventas, Día ST o Sin asignar
- **Semana:** Semana del mes correspondiente

**Organización en GitHub:** Por semana y prioridad

**Archivo generado:** `01-documentacion/plan-del-mes.md`

---

### 2. 🎬 Guía de Producción

**Propósito:** Almacenar los guiones completos listos para producir

**Campos principales:**
- **Nombre:** Título del guion/contenido
- **Línea:** Ventas o Servicio Técnico
- **Fase:** Presentación, Evaluación o Conversión
- **Formato:** Video, Imagen, Carrusel o Slideshow
- **Listo para Producir:** Checkbox (sí/no)

**Contenido especial:**
Cada página en esta base contiene el **guion completo** con:
- 📝 Texto a decir en cámara
- 🎥 B-Roll (tomas de fondo)
- ⚡ Notas de producción
- 🎯 Qué se necesita para grabar
- 💡 Notas importantes

**Organización en GitHub:** Por línea y fase, separando listos de los en preparación

**Archivo generado:** `01-documentacion/guia-produccion.md`

---

### 3. 📊 Base de Datos - Anuncios

**Propósito:** Registro histórico de todos los anuncios publicados con su rendimiento

**Campos principales:**
- **Nombre:** Título del anuncio
- **Línea:** Ventas o Servicio Técnico
- **Fase:** Presentación, Evaluación o Conversión
- **Formato:** Video, Imagen, Carrusel o Slideshow
- **Estado:** Publicado, Borrador o Desactivado
- **Performance:** Excelente, Buena, Funciona, Normal o Mala
- **Notas Performance:** Análisis de por qué funcionó o no
- **Ganador:** 🏆 Checkbox para marcar anuncios destacados
- **Producto/Servicio:** iPhone o servicio asociado
- **Categoría:** Estrategia usada (A-G)
- **Campaña:** A qué campaña pertenece
- **Copy:** Texto del anuncio
- **Fecha Creación:** Cuándo se creó

**Organización en GitHub:**
1. Primero los ganadores 🏆
2. Por línea, fase y estado
3. Ordenados por performance

**Archivo generado:** `01-documentacion/base-datos-anuncios.md`

---

## 🔄 El Workflow Unificado de Sincronización

### ¿Cómo Funciona el Sistema?

El sistema utiliza **un único workflow en n8n** que se ejecuta **cada minuto** y procesa las **3 bases de Notion en paralelo**.

```
       ⏰ TRIGGER (Cada minuto)
              │
    ┌─────────┴─────────┐
    ▼         ▼         ▼
  Flujo 1   Flujo 2   Flujo 3
  (Plan)    (Guía)    (Base)
    │         │         │
    └─────────┴─────────┘
              │
         ✅ Finaliza
```

**Ventaja:** Solo necesitas **1 workflow activo** en lugar de 3 separados, simplificando el mantenimiento y la gestión.

---

### 🎯 Flujo 1: Plan del Mes → GitHub

**Proceso:**
1. 📥 **Obtiene** todos los contenidos de "Plan del Mes" en Notion
2. 🔄 **Transforma** los datos a formato Markdown organizado por semana y prioridad
3. 🔍 **Verifica** si el archivo existe en GitHub
4. ⚖️ **Compara** el contenido nuevo vs. el existente (ignorando timestamps)
5. ✅ **Solo actualiza** si detecta cambios reales en el contenido
6. 📤 **Sube/actualiza** el archivo en GitHub
7. 📱 **Envía** notificación a WhatsApp confirmando la sincronización

**Salida:** `01-documentacion/plan-del-mes.md`
- Organizado por semanas (Semana 1, 2, 3, 4)
- Dentro de cada semana: por prioridad (Alta, Media, Baja)
- Incluye estadísticas completas y barra de progreso

---

### 🎬 Flujo 2: Guía de Producción → GitHub

**Proceso:**
1. 📥 **Obtiene** todos los guiones de "Guía de Producción"
2. 📄 **Extrae** el contenido completo del campo "Guion" de cada página
3. 📝 **Procesa** el guion completo (texto, notas, B-roll, etc.)
4. 🔄 **Transforma** todo a formato Markdown estructurado
5. 🔍 **Verifica** cambios en GitHub
6. ⚖️ **Compara** contenido (ignorando timestamps)
7. ✅ **Solo actualiza** si hay cambios reales
8. 📤 **Sube/actualiza** el archivo en GitHub
9. 📱 **Envía** notificación a WhatsApp

**Salida:** `01-documentacion/guia-produccion.md`
- Organizado por línea (Ventas / Servicio Técnico)
- Dentro de cada línea: por fase (Presentación, Evaluación, Conversión)
- Separado en: ✅ Listos para Producir y ⏳ En Preparación
- Incluye el guion completo de cada contenido

---

### 📊 Flujo 3: Base de Datos Anuncios → GitHub

**Proceso:**
1. 📥 **Obtiene** todos los anuncios de "Base de Datos - Anuncios"
2. 🏆 **Identifica** anuncios ganadores (checkbox "Ganador")
3. 📊 **Organiza** por línea, fase, estado y performance
4. 🔄 **Transforma** a formato Markdown con estadísticas completas
5. 🔍 **Verifica** cambios en GitHub
6. ⚖️ **Compara** contenido (ignorando timestamps)
7. ✅ **Solo actualiza** si hay cambios reales
8. 📤 **Sube/actualiza** el archivo en GitHub
9. 📱 **Envía** notificación a WhatsApp

**Salida:** `01-documentacion/base-datos-anuncios.md`
- Primero muestra los 🏆 ANUNCIOS GANADORES
- Luego organiza por línea, fase y estado
- Ordenados por performance (Excelente → Mala)
- Incluye estadísticas completas, tasa de éxito y análisis de rendimiento

---

## 💡 Ventajas del Workflow Unificado

### ¿Por Qué Un Solo Workflow en Lugar de 3?

#### ✅ **Más Simple de Mantener**
- Solo 1 workflow que activar/desactivar
- Solo 1 lugar donde revisar logs
- Solo 1 configuración de trigger (cada minuto)

#### ✅ **Ejecución Eficiente**
- Los 3 flujos se ejecutan **en paralelo** (al mismo tiempo)
- No esperan uno al otro
- Aprovecha mejor los recursos de n8n

#### ✅ **Lógica Más Clara**
```
Antes (3 workflows):
- Workflow "Plan del Mes" → Cada minuto
- Workflow "Guía Producción" → Cada minuto
- Workflow "Base Datos" → Cada minuto
❌ 3 lugares diferentes, 3 configuraciones

Ahora (1 workflow):
- Workflow unificado → Cada minuto
  ↳ Procesa las 3 bases en paralelo
✅ Un solo lugar, una configuración
```

#### ✅ **Más Fácil de Entender**
El flujo es lineal y predecible:
1. ⏰ **Trigger cada minuto** → Activa todo el workflow
2. 🔄 **3 lecturas en paralelo** → Lee las 3 bases de Notion simultáneamente
3. 📝 **3 transformaciones** → Convierte cada base a su formato Markdown
4. 🔍 **3 comparaciones** → Verifica cambios en GitHub para cada archivo
5. ✅ **3 actualizaciones** → Solo sube si hay cambios reales
6. 📱 **3 notificaciones** → WhatsApp confirma cada sincronización exitosa

#### ✅ **Menos Propenso a Errores**
- Si un flujo falla, los otros 2 continúan funcionando
- El trigger único garantiza que todos se ejecuten juntos
- Menos posibilidad de desincronización de horarios

### ¿Cómo Se Ve en n8n?

```
[Schedule Trigger: Cada minuto]
         │
    ┌────┴────┬────────────┬───────────────┐
    │         │            │               │
[📅 Plan] [🎬 Guía] [📊 Base]            │
    │         │            │               │
[Transform] [Transform] [Transform]       │
    │         │            │               │
[GitHub] [GitHub] [GitHub]                │
    │         │            │               │
[WhatsApp] [WhatsApp] [WhatsApp]          │
    │         │            │               │
    └─────────┴────────────┴───────────────┘
                   │
              [Finaliza]
```

Cada columna funciona de forma **independiente y en paralelo**, pero todas comparten el mismo trigger inicial.

---

## 📝 Estructura de los Documentos Generados

### Plan del Mes (plan-del-mes.md)

```
# 📅 PLAN DEL MES - PRODUCCIÓN DE CONTENIDO

📊 Total de contenidos: X
✅ Completados: Y
📈 Progreso: Z%

## 📆 SEMANA 1
### 🔴 Prioridad Alta
- Contenido 1 (detalles)
- Contenido 2 (detalles)

### 🟡 Prioridad Media
...

## 📊 ESTADÍSTICAS
- Por Estado
- Por Línea
- Por Formato
- Por Producto
- Progreso General
```

---

### Guía de Producción (guia-produccion.md)

```
# 🎬 GUÍA DE PRODUCCIÓN

📊 Total de contenidos: X
✅ Listos para producir: Y

## 🛒 VENTAS
### 🔍 Evaluación

#### ✅ Listos para Producir (X)
##### Nombre del Guion

**Formato:** 🎥 Video

**GUION COMPLETO:**
[Todo el contenido del guion completo]
- Texto a decir
- B-Roll
- Notas
- Requisitos

---

#### ⏳ En Preparación (X)
...

## 📊 ESTADÍSTICAS
- Por Estado de Preparación
- Por Línea
- Por Formato
```

---

### Base de Datos Anuncios (base-datos-anuncios.md)

```
# 📊 BASE DE DATOS - ANUNCIOS

📊 Total de anuncios: X
🏆 Ganadores: Y
📈 Tasa de éxito: Z%

## 🛒 VENTAS

### 🏆 ANUNCIOS GANADORES
- Anuncio ganador 1 (detalles completos)
- Anuncio ganador 2 (detalles completos)

### 👋 Presentación
#### ✅ Publicado
##### Nombre del Anuncio
- Performance: 🌟 Excelente
- Notas: Por qué funcionó
- Categoría, Campaña, etc.

## 📊 ESTADÍSTICAS
- Por Estado
- Por Performance
- Por Formato
- Por Categoría
- Tasa de Éxito
```

---

## 🔔 Sistema de Notificaciones WhatsApp

### Cuándo se envían notificaciones:

**Al crear un archivo nuevo:**
```
✅ [Nombre] sincronizada!
📄 Archivo creado
📊 Total: X contenidos
✅ [Métrica]: Y
🔗 Ver: [Link directo a GitHub]
```

**Al actualizar un archivo existente:**
```
✅ [Nombre] actualizada!
📄 Archivo: nombre.md
📦 Tamaño: X bytes
📊 Total: Y contenidos
✅ [Métrica]: Z
🔗 Ver: [Link directo a GitHub]
```

### Número destino:
573197504788 (WhatsApp de Sebastian)

---

## ⚙️ Características Inteligentes del Sistema

### 1. Detección Inteligente de Cambios

El sistema **NO hace commits innecesarios**. Antes de actualizar GitHub:

✅ Compara el contenido nuevo vs. el existente
✅ Ignora diferencias de timestamps
✅ Normaliza espacios y saltos de línea
✅ Solo actualiza si hay cambios REALES en el contenido

### 2. Manejo de Creación vs. Actualización

- **Si el archivo NO existe:** Lo crea
- **Si el archivo existe:** Lo actualiza con el SHA correcto
- Evita conflictos y sobrescrituras

### 3. Sincronización en Tiempo Real

- Ejecuta cada minuto
- Cambios en Notion → Aparecen en GitHub en máximo 60 segundos
- Documentación siempre actualizada

### 4. Extracción Completa de Contenido (Guía de Producción)

Para cada guion:
- Obtiene las propiedades básicas (nombre, línea, fase, formato)
- **ADEMÁS:** Hace una llamada extra para obtener el contenido completo
- Extrae TODO el texto de la página: headings, párrafos, listas, código
- Lo formatea bonito en el markdown final

---

## 📂 Ubicación de los Archivos en GitHub

### Repositorio
`mrmanzana22/Marketing_project_documentation`

### Carpeta
`01-documentacion/`

### Archivos generados:
1. `01-documentacion/plan-del-mes.md`
2. `01-documentacion/guia-produccion.md`
3. `01-documentacion/base-datos-anuncios.md`

### URLs directas:
- Plan del Mes: `https://github.com/mrmanzana22/Marketing_project_documentation/blob/main/01-documentacion/plan-del-mes.md`
- Guía de Producción: `https://github.com/mrmanzana22/Marketing_project_documentation/blob/main/01-documentacion/guia-produccion.md`
- Base de Datos: `https://github.com/mrmanzana22/Marketing_project_documentation/blob/main/01-documentacion/base-datos-anuncios.md`

---

## 🔐 Credenciales y Configuración

### Notion API
- **Token:** Configurado en n8n
- **Database IDs:**
  - Plan del Mes: `293c2c61-6be1-8169-983b-fdc721c092b1`
  - Guía de Producción: `293c2c61-6be1-818f-a0bd-c1777b1318c0`
  - Base de Datos Anuncios: `293c2c61-6be1-81aa-9db8-e8aaaf69bb28`

### GitHub API
- **Usuario:** mrmanzana22
- **Repositorio:** Marketing_project_documentation
- **Branch:** main
- **Credenciales:** Configuradas en n8n

### Evolution API (WhatsApp)
- **Instancia:** Mr manzana222
- **Número destino:** 573197504788
- **Credenciales:** Configuradas en n8n

---

## 📊 Estadísticas que se Generan Automáticamente

### Plan del Mes:
- Total de contenidos planificados
- Contenidos por estado (Por Hacer, En Preparación, etc.)
- Contenidos por línea (Ventas vs. ST)
- Contenidos por prioridad (Alta, Media, Baja)
- Contenidos por formato (Video, Imagen, etc.)
- Progreso general (% completado)
- Barra de progreso visual

### Guía de Producción:
- Total de contenidos en guía
- Listos para producir vs. En preparación
- Contenidos por línea
- Contenidos por formato
- Porcentaje de preparación
- Barra de progreso visual

### Base de Datos Anuncios:
- Total de anuncios
- Anuncios ganadores 🏆
- Anuncios por estado (Publicado, Borrador, Desactivado)
- Anuncios por performance (Excelente, Buena, etc.)
- Anuncios por formato
- Top 5 categorías más usadas
- Top 5 productos/servicios más promocionados
- Anuncios por campaña
- **Tasa de éxito** (% de anuncios exitosos)
- Barra de progreso de rendimiento

---

## 🎯 Casos de Uso

### 1. Planificación de Contenido
**Actor:** Sebastián (Content Manager)

**Flujo:**
1. Abre Notion → "Plan del Mes"
2. Agrega un nuevo contenido con todos los detalles
3. Automáticamente (máx. 60 seg) → GitHub se actualiza
4. Recibe notificación en WhatsApp confirmando la sincronización
5. Puede compartir el link de GitHub con el equipo

---

### 2. Preparar Guion para Producción
**Actor:** Equipo de Producción

**Flujo:**
1. Abre Notion → "Guía de Producción"
2. Crea una página nueva con el nombre del contenido
3. Escribe TODO el guion completo (texto, B-roll, notas)
4. Marca "Listo para Producir" cuando esté completo
5. Automáticamente → GitHub se actualiza con el guion completo
6. El equipo de producción puede ver el guion en GitHub
7. Al grabar, usan el documento de GitHub como referencia

---

### 3. Registrar Anuncio Publicado
**Actor:** Sebastián (Media Buyer)

**Flujo:**
1. Publica un anuncio en Facebook/Instagram
2. Abre Notion → "Base de Datos - Anuncios"
3. Registra el anuncio con todos los detalles
4. Después de unos días, actualiza el campo "Performance"
5. Agrega "Notas Performance" con el análisis
6. Si es ganador, marca el checkbox "Ganador" 🏆
7. Automáticamente → GitHub se actualiza
8. Puede revisar estadísticas históricas en el documento

---

### 4. Revisar Rendimiento General
**Actor:** Sebastián o equipo

**Flujo:**
1. Abre GitHub → `base-datos-anuncios.md`
2. Ve las estadísticas automáticas:
   - Tasa de éxito general
   - Formatos que mejor funcionan
   - Categorías más efectivas
   - Anuncios ganadores para replicar
3. Toma decisiones basadas en datos históricos

---

## 🚀 Ventajas del Sistema

### ✅ Automatización Total
- Cero intervención manual
- Sincronización en tiempo real
- Sin posibilidad de olvidos

### ✅ Centralización
- Una fuente de verdad (Notion)
- Documentación siempre actualizada (GitHub)
- Accesible desde cualquier lugar

### ✅ Trazabilidad
- Historial completo en GitHub (commits)
- Notificaciones de cada cambio
- Registro de cuándo y qué se modificó

### ✅ Colaboración
- Equipo puede ver documentación en GitHub
- Formato Markdown fácil de leer
- Links directos compartibles

### ✅ Análisis de Datos
- Estadísticas automáticas
- Métricas de rendimiento
- Identificación de patrones de éxito

### ✅ Documentación Completa
- Guiones detallados disponibles
- Planificación visible
- Historial de anuncios organizado

---

## 🔧 Mantenimiento

### Workflow Activo en n8n:

**Nombre:** Sistema de Sincronización Notion → GitHub

**Estado:** ✅ Debe estar ACTIVO

**Frecuencia:** Cada minuto (cron: `* * * * *`)

**Contiene:**
- 3 nodos de Notion (uno por cada base de datos)
- 3 flujos de procesamiento en paralelo
- Nodos de GitHub para crear/actualizar archivos
- Notificaciones WhatsApp por cada sincronización exitosa

### Estado Ideal:
- El workflow debe estar **ACTIVO** (botón verde en n8n)
- Ejecutándose cada minuto automáticamente
- Sin errores en el log de ejecución
- Los 3 flujos procesándose en paralelo sin bloqueos

### Verificación Rápida:
1. **Hacer un cambio** en cualquiera de las 3 bases de Notion
2. **Esperar máximo 60 segundos**
3. **Revisar GitHub** → Debe aparecer el commit con el cambio
4. **Verificar WhatsApp** → Debe llegar notificación automática

### Monitoreo de Logs:
En n8n, buscar en el historial de ejecuciones:
- ✅ **Verde:** Ejecución exitosa (todo sincronizado)
- 🟡 **Amarillo:** Sin cambios detectados (normal)
- ❌ **Rojo:** Error en algún flujo (revisar logs)

---

## 📞 Soporte

Si algo no funciona:

1. **Revisar logs en n8n** → Ver qué paso falló
2. **Verificar credenciales** → Notion API, GitHub API, Evolution API
3. **Probar manualmente** → Ejecutar workflow manualmente en n8n
4. **Revisar permisos** → Notion debe tener acceso a las bases de datos

---

**Sistema creado:** Octubre 2025
**Última actualización:** 24 Octubre 2025
**Versión:** 2.0 (Workflow Unificado)
**Creado por:** Claude Code + Sebastián (Mr. Manzana)

---

## 📋 Changelog

### v2.0 - 24 Octubre 2025
- ✅ **Unificación de workflows:** Los 3 workflows separados ahora son uno solo
- ✅ **Ejecución en paralelo:** Procesamiento simultáneo de las 3 bases
- ✅ **Mantenimiento simplificado:** Solo 1 workflow que gestionar
- ✅ **Mejor documentación:** Explicación clara de la lógica del sistema

### v1.0 - Octubre 2025
- ✅ Sistema inicial con 3 workflows independientes
- ✅ Sincronización automática cada minuto
- ✅ Notificaciones WhatsApp
