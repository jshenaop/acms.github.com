# ACMs — LaCasaMía

Repositorio público de **Análisis Comparativos de Mercado (ACM)** generados por la plataforma [LaCasaMía](https://github.com/jshenaop/lacasamia-realtor-database).

🌐 **Dominio**: https://dot.lacasamia.co
📂 **Source**: https://github.com/jshenaop/lacasamia-realtor-database

Cada subcarpeta es un ACM autocontenido (HTML + imagen Open Graph). GitHub Pages los sirve en `https://dot.lacasamia.co/<slug>/`.

---

## 📊 Última versión por propiedad y tipo

Esta tabla muestra **el ACM más reciente para cada combinación (propiedad, tipo)**. Es la versión vigente — la que debe usarse en conversaciones activas con clientes. Las versiones anteriores quedan en el [Historial de revisiones](#-historial-de-revisiones) abajo.

| Propiedad | Tipo | Comparables | Fecha publicación | Enlace |
|---|---|---|---|---|
| Balcones de Emaús (Los Rosales / Chapinero) | 🛒 Comprador | 34 | 2026-04-24 09:04 | [Ver →](https://dot.lacasamia.co/balcones-de-emaus-comprador-240903/) |
| Balcones de Emaús (Chapinero) | 🏷️ Venta | 18 | 2026-04-04 00:01 | [Ver →](https://dot.lacasamia.co/balcones-de-emaus-040001/) |
| El Peñón — Casa 127 (Girardot) | 🏷️ Venta | — | 2026-04-05 22:31 | [Ver →](https://dot.lacasamia.co/penon-casa-127-052230/) |
| Casa 198 Las Margaritas — 328 m² (Cn. El Peñón, Girardot) | 🏷️ Venta | 56 | 2026-04-05 22:31 | [Ver →](https://dot.lacasamia.co/penon-las-margaritas-052230/) |
| Casa 198 Las Margaritas — 500 m² (Cn. El Peñón, Girardot) | 🏷️ Venta | 56 | 2026-04-05 22:21 | [Ver →](https://dot.lacasamia.co/penon-las-margaritas-052219/) |

> ⚠️ Para encontrar el ACM más actualizado de una propiedad, esta tabla es la fuente de verdad. Si hay una versión más nueva, debería aparecer aquí (no en el historial).

---

## 🕓 Historial de revisiones

Versiones anteriores. **No usar para conversaciones activas** — son referencia histórica.

| Propiedad | Tipo | Fecha | Notas | Enlace |
|---|---|---|---|---|
| Balcones de Emaús | 🛒 Comprador | 2026-04-23 20:50 | 18 comparables (versión previa a la actualización a 34) | [Ver →](https://dot.lacasamia.co/balcones-de-emaus-comprador-232049/) |
| Balcones de Emaús | 🏷️ Venta | 2026-04-03 22:53 | 39 comparables (antes del filtrado a 18 dentro de 1km) | [Ver →](https://dot.lacasamia.co/balcones-de-emaus-032253/) |
| El Peñón — Casa 127 | 🏷️ Venta | 2026-04-05 22:21 | Slug con ortografía pre-corrección (`penol-` → `penon-`) | [Ver →](https://dot.lacasamia.co/penol-casa-127-052219/) |
| Casa 198 Las Margaritas — 328 m² | 🏷️ Venta | 2026-04-03 23:38 | Slug pre-corrección (`penol-`) | [Ver →](https://dot.lacasamia.co/penol-las-margaritas-032338/) |
| Casa 198 Las Margaritas — 500 m² | 🏷️ Venta | 2026-04-03 23:53 | Slug pre-corrección (`penol-`) | [Ver →](https://dot.lacasamia.co/penol-las-margaritas-500m2-032353/) |

**Cómo se actualiza esta tabla**: cuando publicás una nueva versión de un ACM, mové la entrada anterior de "Última versión" al "Historial de revisiones" con una nota corta indicando qué cambió (más comparables, corrección de ortografía, datos actualizados, etc.).

---

## 🧭 Tipos de ACM

| Tipo | Audiencia | Diferencia clave |
|---|---|---|
| **Venta** | Vendedor / agente | Incluye sección de **Recomendación Estratégica de Precio** con precio sugerido, mín. y máx., y análisis cualitativo. |
| **Comprador** | Cliente comprador | Sanitiza el ACM de venta: **elimina la recomendación estratégica** y **renombra los tiers** (ver abajo) para reforzar confianza. |

Existen también dos variantes de **Búsqueda** (sin inmueble objetivo, análisis de mercado de zona):
- **Búsqueda – Compra**: cliente buscando comprar.
- **Búsqueda – Arriendo**: cliente buscando arrendar.

Estas todavía no se han publicado en este repo, pero el pipeline ya las soporta.

---

## 🎯 Sistema de Tiers — cómo se clasifican los comparables

Cada ACM clasifica las propiedades comparables en **dos niveles según distancia al inmueble objetivo (subject)**:

### Tier 1 — Altamente Comparable (core)
- **Distancia**: ≤ 500 metros del subject (radio core).
- **Criterio**: mismo barrio o esquina inmediata → contexto urbano idéntico.
- **Peso en el análisis**: alto. Forma el núcleo de la recomendación.
- **Color en la tabla**: naranja `#FFA522` (acento de marca).

### Tier 2 — Comparable
- **Distancia**: entre 500 m y el radio total de búsqueda (típicamente 1 km, configurable).
- **Criterio**: zona ampliada — mismo sector urbano, validación de tendencia.
- **Peso en el análisis**: menor que Tier 1, pero relevante para detectar outliers.
- **Color en la tabla**: azul navy `#1B2547`.

### Renombre en la versión Comprador
Para los ACMs tipo **Comprador**, los tiers se renombran a un lenguaje más contundente:

| ACM Venta | ACM Comprador |
|---|---|
| Comparable (core ≤ 500m) | **Altamente Comparable** |
| Cercana (500m – 1km) | **Comparable** |

El objetivo es reforzar al comprador que los datos mostrados son realmente comparables — no "cercanas".

---

## ⚙️ Filtros aplicados antes del scoring

Antes de asignar tiers, el pipeline filtra el universo de comparables:

| Filtro | Criterio |
|---|---|
| Tipo de inmueble | Igualdad estricta (apartamento ≠ casa ≠ lote). |
| Tipo de negocio | Igualdad estricta (venta ≠ arriendo). |
| Confianza geocodificación | Solo `alto` y `medio` (descarta `bajo` y `fallido`). |
| Estado en pipeline | `aprobado` (auto) o `extraido` (incluye no-aprobadas aún). |
| Outliers precio/m² | **Arriendo**: 10.000 – 500.000 COP/m²/mes · **Venta**: 1.000.000 – 50.000.000 COP/m² |
| Filtros opcionales | área mínima/máxima, habitaciones (rango), baños (rango), estrato (rango), precio total. |

---

## 🔄 Cómo se publica un ACM aquí

Los ACMs se generan en el repo `lacasamia-realtor-database` con uno de los 4 agentes ACM:

| Agente | Caso de uso |
|---|---|
| `generador-acm-venta-v4` | Cliente vendedor con UN inmueble específico → precio sugerido |
| `generador-acm-venta-comprador-v4` | Post-procesa un ACM de venta para mostrar al comprador |
| `generador-acm-busqueda-compra-v4` | Cliente buscando comprar en una zona |
| `generador-acm-busqueda-arriendo-v4` | Cliente buscando arrendar en una zona |

Tras generar el HTML, el **skill `publicar-acm`** lo sube a este repo en una carpeta `<slug>-<DDHHMM>/index.html` con su `og-image.jpg` (preview en WhatsApp/Twitter). GitHub Pages sirve cada carpeta en `https://dot.lacasamia.co/<slug>/`.

El slug sigue el patrón:
- **Venta**: `<propiedad>-<DDHHMM>` (ej. `balcones-de-emaus-040001`)
- **Comprador**: `<propiedad>-comprador-<DDHHMM>` (ej. `balcones-de-emaus-comprador-240903`)

Donde `DDHHMM` = día del mes + hora + minuto. Así el último publicado siempre tiene el sufijo numérico más alto del día más reciente.

---

## 📐 Estructura técnica de un ACM

Cada `index.html` es un archivo **autocontenido** (~100 KB) con:

- **Hero**: carrusel de fotos del subject + título + estadísticas.
- **Banner de filtros**: tipo, zona, radio aplicados.
- **Mapa interactivo**: Leaflet con marker del subject + círculos de comparables (color por tier).
- **Boxplot**: distribución de precios/m² con cuartiles.
- **Histograma**: frecuencia de precios.
- **Scatter plot**: relación área vs precio.
- **Tabla de comparables**: con tier, distancia, área, precio, link al portal original.
- **Stats globales**: total, promedio, mediana, P65, mín, máx.
- **Recomendación estratégica** *(solo Venta)*: precio sugerido + análisis cualitativo + estrategias.

Renderizado client-side con **D3.js + Leaflet + H3.js**. Sin backend.

---

## 📝 Licencia
Privado — todos los derechos reservados a LaCasaMía.
