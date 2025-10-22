# 📊 SISTEMA NOTION - ESTRUCTURA DE BASES

**Última actualización:** 22 Octubre 2025
**Total bases:** 3 bases activas

---

## 🗄️ BASE 1: ANUNCIOS PUBLICADOS

**ID:** `293c2c61-6be1-81aa-9db8-e8aaaf69bb28`
**Propósito:** Histórico de anuncios YA publicados
**Registros actuales:** 13

### CAMPOS:
- **Nombre** (título)
- **Línea** (Ventas/Servicio Técnico)
- **Fase** (Presentación/Evaluación/Conversión)
- **Formato** (Video/Imagen/Carrusel/Slideshow)
- **Producto/Servicio** (específico)
- **Estado** (Publicado/Borrador/Desactivado)
- **Campaña** (identificador)
- **Categoría** (A-G según sistema)
- **Performance** (Excelente/Funciona/Normal/Buena/Mala)
- **Notas Performance** (texto largo)
- **Ganador** (checkbox)
- **Fecha Creación** (date)
- **COPY** (texto completo del anuncio)

### USO:
- Consultar antes de crear nuevos anuncios
- Identificar patterns ganadores
- Evitar repetición de ángulos

---

## 📅 BASE 2: PLAN DEL MES

**ID:** `293c2c61-6be1-8169-983b-fdc721c092b1`
**Propósito:** Planificar anuncios POR HACER
**Registros actuales:** Variable

### CAMPOS:
- **Nombre** (título)
- **Línea** (Ventas/Servicio Técnico)
- **Fase** (Presentación/Evaluación/Conversión)
- **Formato** (Video/Imagen/Carrusel/Slideshow)
- **Producto/Servicio**
- **Estado** (Por Hacer/En Preparación/Listo/Producido/Publicado)
- **Semana** (Semana 1/2/3/4)
- **Prioridad** (🔴 Alta/🟡 Media/🟢 Baja)

### ESTADOS WORKFLOW:
1. **Por Hacer** → Necesita guía
2. **En Preparación** → Guía creada
3. **Listo para Producir** → Puede grabarse
4. **Producido** → Grabado/diseñado
5. **Publicado** → Live en Facebook

---

## 🎬 BASE 3: GUÍA DE PRODUCCIÓN

**ID:** `293c2c61-6be1-818f-a0bd-c1777b1318c0`
**Propósito:** Guías detalladas para producir
**Registros actuales:** Se crean según necesidad

### CAMPOS METADATA:
- **Nombre** (título)
- **Línea** (Ventas/Servicio Técnico)
- **Fase** (Presentación/Evaluación/Conversión)
- **Formato** (Video/Imagen/Carrusel/Slideshow)
- **Listo para Producir** (checkbox)

### SECCIONES INTERNAS:
1. **QUÉ DIRÁ EL ANUNCIO**
   - Copy completo
   - Emojis incluidos
   - CTA específico

2. **QUÉ NECESITO**
   - Recursos materiales
   - Productos a mostrar
   - Locaciones

3. **QUÉ VOY A GRABAR/CREAR**
   - Para video: Guion persona + B-roll
   - Para imagen: Composición visual
   - Para carrusel: Contenido por slide

4. **NOTAS IMPORTANTES**
   - Tips de producción
   - Énfasis especiales
   - Recordatorios técnicos

---

## 🔄 FLUJO DE TRABAJO

```
Plan del Mes → Crear guía → Guía Producción
     ↓                           ↓
Producir contenido → Contenido listo
     ↓
Publicar → Base Anuncios
     ↓
Analizar performance → Feedback a Plan
```

---

## 📝 COMANDOS RÁPIDOS NOTION

### CREAR ANUNCIO:
```
1. Agregar fila en "Plan del Mes"
2. Asignar fase, formato, producto
3. Crear guía en "Guía de Producción"
4. Cambiar estado según avance
```

### CONSULTAR PERFORMANCE:
```
1. Ir a "Base de Anuncios"
2. Filtrar por "Ganador" = true
3. Analizar categorías exitosas
4. Replicar patterns ganadores
```

### WORKFLOW COMPLETO:
```
Plan → Guía → Producir → Publicar → Medir
```
