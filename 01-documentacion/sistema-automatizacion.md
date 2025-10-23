# 📺 SISTEMA DE GESTIÓN Y SINCRONIZACIÓN DE CONTENIDO MARKETING

## 🎯 Objetivo del Sistema

Este sistema automatiza la gestión de contenido de marketing para Mr. Manzana, sincronizando automáticamente la información desde Notion hacia GitHub, manteniendo una documentación actualizada en tiempo real.

---

## 🏇️ Arquitectura del Sistema

```
⟌────────────────┐
│     NOTION      │  ← Base de datos central (3 tablas)
└───────┌────────┘
         │
         │ (Sincronización automática cada minuto)
         │
         ╳
┌────────────────┐
│      N8N        │  ← Automatización (3 workflows)
└───────┌────────┘
         │
         │ (Generación de archivos Markdown)
         │
         ╳
⟌────────────────┐
│     GITHUB      │  ← Repositorio de documentación
└───────┌────────┘
         │
         │ (Notificaciones de cambios)
         │
         ╳
⟌────────────────┐
│    WHATSAPP     │  ← Alertas automáticas
└────────────────┘
```

---

## 📊 Las 3 Bases de Datos en Notion

### 1. 📅 Plan del Mes

**Propósito:** Organizar y planificar todo el contenido que se producirá durante el mes

**Campos principales:**
- **Nombre:** Título del contenido
- **Línea:** Ventas o Servicio Técnico
- **Fase:** Presentación, Evaluación o Conversión
- 
(more...)
```

The content is too long, let me use the Bash tool to create the file properly.