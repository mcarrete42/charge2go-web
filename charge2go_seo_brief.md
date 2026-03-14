# charge2go.io — Brief SEO & Conversión para Claude Code
> Objetivo: aumentar tráfico orgánico B2B y convertir propietarios de locales en partners (que soliciten la máquina)

---

## 1. CONTEXTO Y OBJETIVO DE NEGOCIO

**Empresa:** charge2go — servicio de alquiler de power banks mediante máquinas inteligentes instaladas en locales.

**Público objetivo de esta web:** propietarios y managers de negocios con tráfico de personas (bares, restaurantes, cafeterías, hoteles, gimnasios, centros comerciales, hospitales, eventos).

**Conversión deseada:** que el propietario del local rellene el formulario de contacto para solicitar la instalación de una máquina **gratis**.

**Mensaje central a transmitir:**
> "Ofrece a tus clientes un servicio que necesitan, sin coste para ti. Más motivos para quedarse = más consumo = más ingresos."

**Tono:** profesional, directo, moderno. Nada corporativo. Hablar de tú al propietario del local.

---

## 2. DIAGNÓSTICO SEO ACTUAL

### Problemas críticos identificados

#### 2.1 H1 no tiene valor SEO
```html
<!-- ACTUAL (solo branding, sin keywords) -->
<h1>Batería, <em>justo cuando</em> la necesitas.</h1>

<!-- PROPUESTO -->
<h1>Instala una máquina de carga de móviles en tu local — gratis y sin gestión.</h1>
```

#### 2.2 Title tag mejorable
```html
<!-- ACTUAL -->
<title>charge2go — Pide una máquina de alquiler de power banks gratis</title>

<!-- PROPUESTO -->
<title>charge2go | Máquina de carga de móviles gratis para tu local — Más clientes, más ingresos</title>
```

#### 2.3 Meta description ausente o genérica
```html
<!-- PROPUESTA -->
<meta name="description" content="Instala gratis una máquina de alquiler de power banks en tu bar, restaurante o gimnasio. Tus clientes se quedan más tiempo, tú generas ingresos sin inversión ni gestión. charge2go." />
```

#### 2.4 Las estadísticas están renderizadas solo por JavaScript
Los contadores animados (15%, 25%, 46%) no son indexables si solo existen en JS.

**Solución:** añadir los valores como texto estático en el HTML antes de que el JS los sobreescriba, o asegurar que el valor final queda en el DOM como texto visible.

```html
<!-- Asegurar que el HTML base contenga el valor final, no "0%" -->
<span class="stat-number" data-target="15">15</span>%
```

#### 2.5 Sin schema markup
Añadir al `<head>`:
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "charge2go",
  "description": "Servicio de alquiler de power banks mediante máquinas inteligentes para negocios en España.",
  "url": "https://charge2go.io",
  "telephone": ["+34638314792", "+34687242903"],
  "email": "hola@charge2go.io",
  "areaServed": "ES",
  "serviceType": "Alquiler de power banks"
}
```

También añadir schema de tipo `FAQPage` en la sección de preguntas frecuentes (ver sección 4).

#### 2.6 Sin blog / contenido de atracción
La web es solo una landing. Google no tiene motivo para indexarla repetidamente ni para posicionarla en búsquedas informacionales. Necesita un blog orientado a propietarios de negocios (ver sección 5).

#### 2.7 La marca "charge2go" no aparece en Google
Búsqueda de `"charge2go" España` no devuelve resultados del dominio. Autoridad de dominio prácticamente 0. Prioridad urgente: conseguir menciones y backlinks desde directorios, medios sectoriales y redes sociales.

---

## 3. CAMBIOS EN LA LANDING PRINCIPAL (index.html)

### 3.1 Hero section — Reescribir copy con foco en el propietario

**Mensaje clave:** el beneficio no es "dar carga a tus clientes", es "que tus clientes se queden más tiempo y consuman más".

```
HEADLINE PROPUESTO:
"El servicio que hace que tus clientes se queden más tiempo. Sin coste."

SUBHEADLINE:
"Instala una máquina de alquiler de power banks en tu local. 
Tus clientes cargan su móvil, tú generas ingresos pasivos — sin inversión, sin gestión, sin complicaciones."

CTA PRINCIPAL:
"Quiero una máquina gratis →"
```

### 3.2 Sección de estadísticas — Hacerlas más impactantes para el propietario

Reformular el contexto de cada stat para que el propietario entienda el impacto directo en su negocio:

```
15% de tus clientes se van antes si no pueden cargar el móvil.
→ Cada 100 clientes, pierdes 15 por algo que tiene solución en 30 minutos.

25% si tu negocio atrae a menores de 30 años.
→ El público joven es el más rentable... y el primero en irse sin batería.

46% se quedaría más tiempo si pudieran cargar.
→ Más tiempo = más consumo. El ROI de una máquina charge2go es inmediato.
```

### 3.3 Sección "Para partners" — Reforzar el mensaje sin coste / sin riesgo

Añadir o reformular los 4 puntos con foco en eliminar objeciones:

```
✓ INSTALACIÓN GRATIS EN MENOS DE 30 MIN
Solo necesita un enchufe estándar. Sin obras, sin técnicos, sin permisos especiales.

✓ CERO INVERSIÓN, CERO COSTES FIJOS
No pagas nada. Nunca. Te llevas un porcentaje de cada alquiler, transparente y mensual.

✓ TU EQUIPO NO HACE NADA
La atención al usuario, las incidencias y la reposición las gestiona charge2go. 
Ni siquiera para responder un "¿me cargas el móvil?".

✓ CONTROL TOTAL SIN ESFUERZO
Dashboard con datos de uso e ingresos. Tú ves lo que genera la máquina, en tiempo real.
```

### 3.4 Añadir sección de FAQ (nueva) — Doble objetivo: SEO + conversión

Posicionar en búsquedas de long-tail y responder objeciones antes de que el propietario las tenga.

```html
<!-- Sección FAQ — añadir antes del formulario de contacto -->

<section id="faq">
  <h2>Preguntas frecuentes</h2>

  <details>
    <summary>¿Cuánto me cuesta instalar la máquina en mi local?</summary>
    <p>Nada. La instalación, la máquina y el mantenimiento son completamente gratuitos para el local. charge2go corre con todos los costes. Tú solo pones el espacio y un enchufe estándar.</p>
  </details>

  <details>
    <summary>¿Cuánto espacio ocupa la máquina?</summary>
    <p>La estación tiene un footprint reducido, similar a una papelera de oficina. Cabe en cualquier barra, mostrador o rincón con tráfico de clientes.</p>
  </details>

  <details>
    <summary>¿Qué tiene que hacer mi personal?</summary>
    <p>Nada. Literalmente. La máquina funciona de forma autónoma. El usuario elige, paga en contactless y recoge la power bank. Si hay alguna incidencia, la gestiona el equipo de charge2go directamente con el usuario.</p>
  </details>

  <details>
    <summary>¿Cuánto dinero puede generar mi local?</summary>
    <p>Depende del tráfico de tu negocio. Con un volumen medio de clientes, la máquina genera ingresos pasivos mensuales desde el primer día. Te lo detallamos sin compromiso cuando nos contactes.</p>
  </details>

  <details>
    <summary>¿Qué pasa si la máquina tiene una avería?</summary>
    <p>El sistema está monitorizado en remoto 24/7. charge2go detecta las incidencias antes que tú y gestiona la resolución. Tu negocio no se ve afectado.</p>
  </details>

  <details>
    <summary>¿Tengo que instalar alguna app o sistema especial?</summary>
    <p>No. La máquina solo necesita un enchufe estándar de 220V. No requiere instalación de red, software ni ningún tipo de integración con tus sistemas.</p>
  </details>

  <details>
    <summary>¿Puedo retirar la máquina si dejo de quererla?</summary>
    <p>Sí. Sin permanencia ni penalización. Acordamos las condiciones de salida de forma transparente desde el inicio.</p>
  </details>
</section>
```

### 3.5 Añadir sección de sectores con páginas individuales (o anclas con contenido)

Actualmente los sectores son solo iconos. Ampliar con una frase de beneficio específico por sector:

```
HOSTELERÍA Y RESTAURANTES
"Tus clientes piden una copa más si tienen el móvil cargado. Así de sencillo."

BARES Y DISCOTECAS
"A las 2AM la batería muere. Con charge2go, tus clientes se quedan hasta el final."

GIMNASIOS
"El entreno dura más cuando no hay que preocuparse por la batería. Ofrece eso."

HOTELES
"Un servicio de valor añadido en recepción o lobby, sin coste operativo."

HOSPITALES Y CLÍNICAS
"Familias en espera con el móvil muerto. Dales tranquilidad con un servicio que cuida."

EVENTOS Y FESTIVALES
"El momento más viral de un evento necesita batería. Asegúrala."
```

### 3.6 Añadir testimonios / prueba social (placeholder si aún no hay)

```html
<section id="testimonios">
  <h2>Lo que dicen nuestros partners</h2>
  <!-- Añadir cards con nombre del local, ciudad, tipo de negocio y cita breve -->
  <!-- Si no hay testimonios reales aún, preparar el componente para añadirlos -->
</section>
```

---

## 4. NUEVAS PÁGINAS A CREAR (para SEO por sector)

Crear páginas de destino individuales para cada sector. Cada página debe tener:
- URL semántica
- H1 con keyword
- Copy específico del beneficio para ese tipo de negocio
- Mismo CTA: formulario de contacto o "Pide tu máquina gratis"

### Páginas prioritarias:

| URL | H1 sugerido | Keyword objetivo |
|-----|-------------|-----------------|
| `/restaurantes` | "Haz que tus clientes se queden más en tu restaurante — sin coste" | máquina carga móvil restaurante |
| `/bares` | "El servicio que hace que tus clientes no se vayan antes de tiempo" | alquiler power bank bar España |
| `/gimnasios` | "Añade un servicio premium a tu gimnasio sin invertir un euro" | servicio carga móvil gimnasio |
| `/hoteles` | "Mejora la experiencia de tus huéspedes desde el primer check-in" | máquina power bank hotel |
| `/eventos` | "Mantén a tu público conectado y presente hasta el final" | alquiler power banks eventos festivales España |
| `/hospitales-clinicas` | "Un servicio esencial para familias en espera, sin gestión para tu equipo" | carga móvil hospitales clínicas |

---

## 5. BLOG — PLAN DE CONTENIDOS (primeros 3 artículos)

Crear sección `/blog` con los siguientes artículos. Objetivo: atraer propietarios de negocios que buscan ideas para mejorar su local o aumentar ingresos.

### Artículo 1
- **URL:** `/blog/como-hacer-que-tus-clientes-se-queden-mas-tiempo`
- **Title:** "5 formas de hacer que tus clientes se queden más tiempo en tu bar o restaurante"
- **Keyword principal:** cómo retener clientes en hostelería
- **Ángulo:** listicle práctico. charge2go aparece como solución #1 o #2, de forma natural.
- **CTA al final:** "Instala gratis una máquina charge2go en tu local →"

### Artículo 2
- **URL:** `/blog/servicios-gratuitos-para-tu-negocio-que-fidelizan-clientes`
- **Title:** "Servicios gratuitos que puedes ofrecer en tu negocio para fidelizar clientes en 2025"
- **Keyword principal:** servicios gratuitos negocios hostelería
- **Ángulo:** incluir WiFi, carga de móvil, agua, etc. charge2go como el más rentable porque genera ingresos.

### Artículo 3
- **URL:** `/blog/ingresos-extra-sin-inversion-para-tu-local`
- **Title:** "Cómo generar ingresos extra en tu local sin invertir ni un euro"
- **Keyword principal:** ingresos extra negocio hostelería sin inversión
- **Ángulo:** charge2go como caso de estudio central. Incluir las estadísticas del brochure.

---

## 6. SEO TÉCNICO — CHECKLIST COMPLETO

### Meta tags (en `<head>`)
```html
<!-- Title: máximo 60 caracteres -->
<title>charge2go | Máquina de carga gratis para tu local — Sin inversión</title>

<!-- Description: máximo 155 caracteres -->
<meta name="description" content="Instala gratis una estación de alquiler de power banks en tu bar, restaurante o gimnasio. Tus clientes se quedan más, tú ganas sin gestión. charge2go." />

<!-- Open Graph (para compartir en redes) -->
<meta property="og:title" content="charge2go — Instala una máquina de carga de móviles gratis en tu local" />
<meta property="og:description" content="El 46% de tus clientes se quedaría más tiempo si pudiera cargar el móvil. Dales ese servicio sin coste para ti." />
<meta property="og:image" content="https://charge2go.io/assets/images/og-image.jpg" />
<meta property="og:url" content="https://charge2go.io" />
<meta property="og:type" content="website" />
<meta property="og:locale" content="es_ES" />

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="charge2go — Máquina de carga gratis para tu local" />
<meta name="twitter:description" content="Sin inversión, sin gestión. Tus clientes se quedan más tiempo y tú generas ingresos pasivos." />
```

### Canonical y hreflang
```html
<link rel="canonical" href="https://charge2go.io/" />
```

### Sitemap.xml
Crear `/sitemap.xml` con todas las URLs del sitio:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://charge2go.io/</loc><priority>1.0</priority></url>
  <url><loc>https://charge2go.io/restaurantes</loc><priority>0.8</priority></url>
  <url><loc>https://charge2go.io/bares</loc><priority>0.8</priority></url>
  <url><loc>https://charge2go.io/gimnasios</loc><priority>0.8</priority></url>
  <url><loc>https://charge2go.io/hoteles</loc><priority>0.8</priority></url>
  <url><loc>https://charge2go.io/eventos</loc><priority>0.8</priority></url>
  <url><loc>https://charge2go.io/hospitales-clinicas</loc><priority>0.7</priority></url>
  <url><loc>https://charge2go.io/blog</loc><priority>0.7</priority></url>
</urlset>
```

### robots.txt
```
User-agent: *
Allow: /
Sitemap: https://charge2go.io/sitemap.xml
```

### Headings — Jerarquía correcta por página

**index.html:**
- `<h1>` → 1 único H1 con keyword principal
- `<h2>` → secciones principales (Los números, Cómo funciona, Para partners, FAQ, Contacto)
- `<h3>` → subsecciones dentro de cada bloque

**Regla:** nunca saltarse niveles (h1 → h3 sin h2).

### Alt text en imágenes
```html
<!-- ACTUAL (bien) -->
<img alt="Estación de alquiler de power banks charge2go instalada en un local" ...>

<!-- Mejorar el de la batería -->
<img alt="Power bank charge2go con cables USB-C, Lightning y micro-USB para cualquier smartphone" ...>

<!-- Añadir al logo -->
<img alt="charge2go — alquiler de power banks para negocios" ...>
```

### Performance
- Verificar que las imágenes estén en formato WebP
- Añadir `loading="lazy"` a imágenes que no están en el viewport inicial
- Asegurar que el CSS crítico está inline o en `<head>` para evitar render-blocking

---

## 7. FORMULARIO DE CONTACTO — OPTIMIZACIÓN PARA CONVERSIÓN

El formulario actual pide: Nombre, Empresa/Local, Tipo de negocio, Teléfono, Email, Mensaje (opcional).

### Cambios propuestos:

1. **Cambiar el headline del formulario:**
   ```
   ACTUAL: "¿Hablamos?"
   PROPUESTO: "Pide tu máquina gratis. Te respondemos en menos de 24h."
   ```

2. **Añadir un elemento de confianza justo encima del botón:**
   ```
   ✓ Sin permanencia   ✓ Sin costes   ✓ Instalación en 30 min
   ```

3. **Cambiar el texto del botón de envío:**
   ```
   ACTUAL: "Enviar mensaje →"
   PROPUESTO: "Quiero mi máquina gratis →"
   ```

4. **Mensaje de confirmación tras envío — mejorar:**
   ```
   ACTUAL: "Mensaje enviado — Te respondemos en menos de 24h."
   PROPUESTO: "¡Perfecto! Hemos recibido tu solicitud. 
   Nuestro equipo te contactará en menos de 24h para coordinar la instalación."
   ```

---

## 8. ESTRATEGIA DE BACKLINKS (off-page SEO)

Acciones para ganar autoridad de dominio desde cero:

### Alta prioridad (hacer esta semana)
- [ ] Dar de alta en **Google Business Profile** (aunque sea un servicio, mejora la visibilidad)
- [ ] Dar de alta en **Bing Webmaster Tools** y **Google Search Console**
- [ ] Dar de alta en directorios: Páginas Amarillas, Hotfrog, Infoisinfo, Kompass España
- [ ] Crear perfil en **LinkedIn** de empresa con enlace a la web
- [ ] Crear perfil en **Instagram** @charge2go con bio y enlace

### Media prioridad (primer mes)
- [ ] Contactar con **blogs de hostelería** en España para aparecer como solución (ej: Gastroactitud, El Tenedor Blog, Hostelería de España)
- [ ] Publicar nota de prensa en **PRnoticias** o **Notas de prensa** (gratuitos)
- [ ] Buscar menciones en **foros de propietarios de bares/restaurantes** en Facebook Groups

### Largo plazo
- [ ] Conseguir reseñas de partners reales en Google
- [ ] Publicar casos de éxito con datos reales (ej: "La cafetería X aumentó su ticket medio un 12% con charge2go")

---

## 9. KEYWORDS OBJETIVO — TABLA COMPLETA

| Keyword | Tipo | Intención | Prioridad |
|---------|------|-----------|-----------|
| máquina alquiler power bank negocio | B2B | Transaccional | 🔴 Alta |
| carga móvil gratis para mi local | B2B | Transaccional | 🔴 Alta |
| instalar máquina carga móvil restaurante | B2B | Transaccional | 🔴 Alta |
| alquiler power bank para bares España | B2B | Transaccional | 🔴 Alta |
| servicio carga móvil gimnasio | B2B | Transaccional | 🟠 Media |
| cómo retener clientes en hostelería | B2B | Informacional | 🟠 Media |
| ingresos extra sin inversión negocio | B2B | Informacional | 🟠 Media |
| alquilar power bank cerca de mí | B2C | Navegacional | 🟡 Baja (secundario) |
| charge2go | Marca | Navegacional | 🟢 Construir |

---

## 10. RESUMEN DE PRIORIDADES PARA CLAUDE CODE

### Sprint 1 — Cambios críticos (máximo impacto, mínimo tiempo)
1. Corregir H1 con keyword B2B
2. Añadir meta title y meta description optimizados
3. Añadir Open Graph tags
4. Asegurar que los contadores (15%, 25%, 46%) están en el HTML estático
5. Añadir schema markup JSON-LD en `<head>`
6. Reescribir el copy del hero con foco en el propietario del local
7. Optimizar el formulario (headline + botón + mensaje post-envío)
8. Crear `sitemap.xml` y `robots.txt`

### Sprint 2 — Contenido y conversión
1. Añadir sección FAQ con schema FAQPage
2. Ampliar sección de sectores con copy específico por tipo de negocio
3. Añadir sección de testimonios (aunque sea vacía con placeholder)
4. Reformular las estadísticas con contexto orientado al propietario

### Sprint 3 — Escalabilidad SEO
1. Crear páginas de sector individuales (`/restaurantes`, `/bares`, `/gimnasios`, etc.)
2. Crear estructura de blog con primer artículo publicado
3. Añadir sección de ciudades si se opera en zonas específicas

---

*Brief preparado para charge2go.io — Marzo 2026*
*Objetivo: posicionar charge2go como la opción preferente para propietarios de negocios que buscan ofrecer carga de móvil a sus clientes sin coste ni gestión.*
