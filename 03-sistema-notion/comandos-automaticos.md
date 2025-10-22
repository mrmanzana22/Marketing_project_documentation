# 🤖 COMANDOS AUTOMÁTICOS PARA IA

**Propósito:** Comandos que el asistente ejecuta automáticamente
**Última actualización:** 22 Octubre 2025

---

## 📝 COMANDOS PRINCIPALES

### COMANDO 1: "Necesito [X] anuncios de [tema]"

**ACCIÓN AUTOMÁTICA:**
```python
1. Crear X filas en "Plan del Mes"
2. Auto-asignar:
   - Línea (detectar si es Ventas o Servicio)
   - Fase (distribuir entre las 3)
   - Formato (variar según performance)
   - Prioridad: 🔴 Alta
   - Estado: "Por Hacer"
3. Confirmar al usuario
```

**EJEMPLO:**
> Usuario: "Necesito 5 anuncios de iPhone 14 Pro"

**RESPUESTA IA:**
```
✅ Creados 5 anuncios en Plan del Mes:
1. Video Presentación - iPhone 14 Pro
2. Imagen Evaluación - iPhone 14 Pro specs
3. Carrusel Evaluación - iPhone 14 Pro vs competencia
4. Video Conversión - iPhone 14 Pro oferta
5. Imagen Conversión - iPhone 14 Pro urgencia
```

---

### COMANDO 2: "Crea las guías para [anuncios]"

**ACCIÓN AUTOMÁTICA:**
```python
1. Por cada anuncio sin guía:
   - Crear página en "Guía de Producción"
   - Generar copy según fase y formato
   - Usar plantillas base
   - NO repetir ángulos recientes
2. Cambiar estado a "En Preparación"
```

---

### COMANDO 3: "Ya [grabé/produje] el anuncio de [X]"

**ACCIÓN AUTOMÁTICA:**
```python
1. Buscar en "Plan del Mes"
2. Cambiar estado → "Producido"
3. Marcar checkbox en Guía
4. Notificar: "Listo para publicar"
```

---

### COMANDO 4: "Ya publiqué el anuncio de [X]"

**ACCIÓN AUTOMÁTICA:**
```python
1. Buscar en "Plan del Mes"
2. Cambiar estado → "Publicado"
3. Crear entrada en "Base de Anuncios"
4. Copiar todo incluyendo COPY
5. Fecha = HOY
```

---

### COMANDO 5: "El anuncio [X] tuvo [performance]"

**ACCIÓN AUTOMÁTICA:**
```python
1. Buscar en "Base de Anuncios"
2. Actualizar Performance
3. Si es "excelente" → Ganador = ✅
4. Agregar notas si las da
```

---

## 🔍 COMANDOS DE CONSULTA

### "Muéstrame qué tengo pendiente"

**RESPUESTA:**
```
📋 RESUMEN DE PENDIENTES:

POR HACER (3):
- Video iPhone 15 Pro
- Imagen cambio batería
- Carrusel garantías

EN PREPARACIÓN (2):
- Video servicio técnico
- Imagen Halloween

LISTOS PARA GRABAR (1):
- Carrusel iPhone 13

PRODUCIDOS (1):
- Video presentación marca
```

---

### "Analiza el performance del mes"

**RESPUESTA:**
```
📊 ANÁLISIS OCTUBRE 2025:

WINNERS: 6/13 (46% win rate)
- Videos: 75% win rate ⭐
- Carruseles: 100% win rate ⭐
- Imágenes: 33% win rate ⚠️

TOP CATEGORÍAS:
1. E-Urgencia (75% winners)
2. A-Garantía (100% winners)
3. D-Experiencia (100% winners)

RECOMENDACIONES:
✅ Más videos y carruseles
✅ Explotar urgencia/escasez
✅ Aumentar servicio técnico
⚠️ Reducir imágenes estáticas
```

---

## ⚡ COMANDOS RÁPIDOS

### "Dame un copy rápido de [producto]"
→ Genera copy sin crear en Notion

### "¿Qué ángulo no he usado?"
→ Analiza últimos 10 y sugiere

### "Revisa el anuncio [X]"
→ Muestra guía completa

### "¿Cuántos anuncios tengo este mes?"
→ Cuenta total y por estado

### "Duplica el anuncio [X] pero para [Y]"
→ Copia estructura, cambia producto

---

## 🚨 VALIDACIONES AUTOMÁTICAS

**ANTES DE CREAR:**
- ✅ No repetir ángulos (10 anuncios)
- ✅ Verificar producto existe
- ✅ Fase apropiada al objetivo

**AL GENERAR COPY:**
- ✅ Incluir garantía SIEMPRE
- ✅ Ubicación correcta
- ✅ CTA con emoji
- ✅ Longitud según formato

**AL PUBLICAR:**
- ✅ Estado correcto en workflow
- ✅ Copy guardado en base
- ✅ Fecha actualizada
