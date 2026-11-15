# Práctica 4.5 – Calculadora de huella ecológica

**Instituto Tecnológico de Mazatlán · Desarrollo Sustentable (ACD-0908) · Unidad 4**
**Carrera:** Ingeniería en Sistemas Computacionales
**Alumno:** Sanchez Gamboa Jesus

## Descripción

Página web con un cuestionario de estilo de vida (alimentación, transporte, energía, consumo y residuos). Los datos se envían a un webhook de Make, una inteligencia artificial (Make AI Agent) estima la huella ecológica y la respuesta se muestra en la misma página: hectáreas globales, planetas necesarios, impacto por área, 3 acciones para reducirla y una oportunidad económica.

**Flujo:** Página web → Webhook de Make → Make AI Agent → Webhook Response → Página web

## Contenido

| Archivo | Descripción |
| --- | --- |
| `index.html` | Página de la calculadora (HTML, CSS y JavaScript en un solo archivo) |
| `imagenes/01_webhook_campos_recibidos.png` | Make recibiendo los 10 campos del cuestionario |
| `imagenes/02_resultado_en_la_pagina.png` | Resultado de la estimación mostrado en la página |
| `resultados.docx` | Documento de Word con lo aprendido en la práctica |
| `video.url` | Acceso directo al video de la práctica |

## Video

https://youtu.be/R0U68xJ7lhw?si=lpD8gnxDDyQqR5y3

## Cómo funciona

1. El usuario contesta 10 preguntas: `carne`, `local`, `transporte`, `km`, `vuelos`, `aire`, `personas`, `ropa`, `celular` y `separa`.
2. Al presionar **Calcular mi huella**, la página envía un `POST` con `fetch` y `URLSearchParams` a la URL del webhook (constante `WEBHOOK_URL` en `index.html`).
3. En Make, el **Make AI Agent** (con Make's AI Provider) recibe los datos y genera la estimación en texto plano.
4. El módulo **Webhook Response** devuelve el texto con los encabezados `Content-Type: text/plain; charset=utf-8` y `Access-Control-Allow-Origin: *`.
5. La página muestra la respuesta respetando los saltos de línea (`white-space: pre-line`).

## Cómo publicarla

1. Sube `index.html` a un repositorio de GitHub.
2. En **Settings → Pages**, elige la rama `main` y la carpeta `/ (root)`.
3. Abre el enlace que genera GitHub Pages.

## Nota

La estimación hecha con IA es aproximada y no es un cálculo oficial. Para comparar, usar la calculadora de Global Footprint Network: https://www.footprintcalculator.org
