---
type: workflow
title: "Flujo de la comprobación de dominio"
description: "Cómo funciona la comprobación gratuita de la portada: normalización del dominio, petición al webhook de auditoría, formato de respuesta que acepta la página, estados que muestra, manejo de errores, modo demostración y preferencia de tema."
tags: [landing-page, email-security, spf, dkim, dmarc, frontend]
verified:
  - by: openwiki/0.6.0
    at: 2026-09-25T11:01:50.364Z
sources:
  - id: openwiki-source-f8d10828394c4129061d5b0e
    resource: repo://index.html
generated: { by: "claude-code", at: "2026-09-25T11:01:50.364Z" }
---

# Flujo de la comprobación de dominio

La portada (`index.html`) ofrece una comprobación gratuita de la protección del
correo de un dominio: SPF, DKIM y DMARC. Todo el comportamiento vive en un
único bloque `<script>` al final del fichero, sin librerías.

## Recorrido

<!-- openwiki: mermaid parse failed and this diagram was converted to a text fence so it does not break rendering. Fix the diagram source and restore the mermaid fence. Parser error: Heuristic: an unescaped angle bracket inside a label breaks rendering; rephrase the label. -->
```text
sequenceDiagram
    participant V as Visitante
    participant P as Portada (index.html)
    participant W as Webhook de auditoría
    V->>P: escribe el dominio y pulsa «Comprobar gratis» o Enter
    P->>P: clean(): normaliza el dominio
    alt sin punto
        P-->>V: pide el dominio completo
    else válido
        P->>W: POST {"domain": "<dominio>"}
        Note over P: espera mínima de 3,2 s en paralelo
        W-->>P: JSON con el resultado
        alt respuesta válida
            P-->>V: tarjetas SPF · DKIM · DMARC y resumen
        else error, rechazo o sin datos
            P-->>V: vuelve al formulario con el motivo
        end
    end
```

### 1. Normalizar el dominio

`clean()` pasa el texto a minúsculas y quita `http(s)://`, `www.`, todo lo que
haya antes de una `@` (así se puede pegar un correo entero), la ruta y el punto
final. Si el resultado no contiene ningún punto, la página pide el dominio
completo y no hace ninguna petición.

### 2. Pedir el análisis

La página muestra una animación de carga y lanza a la vez dos promesas: la
petición al webhook y una espera mínima de 3,2 segundos, para que el resultado
no aparezca de golpe. La petición es un `POST` con cuerpo JSON
`{"domain": "<dominio>"}` a la URL de la constante `WEBHOOK_URL`. Un fallo de
red o una respuesta que no es JSON se trata como «sin datos».

### 3. Interpretar la respuesta

La página acepta varias formas de respuesta:

- si llega un array, usa su primer elemento;
- si el objeto trae una clave `result`, usa su contenido;
- espera claves `spf`, `dkim` y `dmarc`; cada una puede ser un texto de
  estado o un objeto con `status` (o `state` o `result`) y, opcionalmente,
  `detail`, un texto que sustituye a la explicación por defecto.

`norm()` traduce cada estado a uno de tres niveles:

| Nivel | Etiqueta | Valores que lo producen |
|---|---|---|
| `ok` | Protegido | `ok`, `pass`, `valid`, `good`, `reject`, `protected`, `quarantine` o `true` |
| `warn` | A medias | `warn`, `warning`, `partial`, `none`, `monitor`, `p=none`, `soft` |
| `fail` | Desprotegido | cualquier otro valor |

Cada comprobación se pinta como una tarjeta con una explicación llana de qué
es, y un veredicto: el `detail` del servidor si existe o, si no, el texto
fijo de la constante `CHECKS` para ese nivel. El resumen final cuenta las
comprobaciones en `fail` y en `warn` y elige la frase («Hay una puerta
abierta…», «Lo esencial está cubierto…» o «Tu correo está bien protegido…»).

### 4. Errores: nunca datos inventados

Si la respuesta no llega, no es un objeto, trae `ok: false` o no contiene
ninguna de las tres comprobaciones, la página **no muestra resultados**:
vuelve al formulario y enseña el `mensaje` que envíe el servidor (por ejemplo,
dominio inválido o límite de uso) o un texto genérico que invita a reintentar
o a escribir a `info@olibesc.com`. Es una decisión explícita del código: no se
muestran datos de ejemplo sobre un dominio real.

## Modo demostración

Si `WEBHOOK_URL` está vacía, la página no hace ninguna petición y muestra un
resultado de ejemplo fijo (SPF protegido, DKIM a medias, DMARC desprotegido).
Sirve para trabajar el diseño en local sin depender del webhook.

## Preferencia de tema

El botón de tema alterna entre claro y oscuro y guarda la elección en
`localStorage` bajo la clave `olibesc-theme`. Si el navegador bloquea el
almacenamiento, la página sigue funcionando sin recordarlo.

## Dónde tocar

| Para… | Tocar |
|---|---|
| Cambiar el destino del análisis | `WEBHOOK_URL` |
| Cambiar textos de cada comprobación | `CHECKS` |
| Aceptar un estado nuevo del servidor | las listas de `norm()` |
| Cambiar colores o etiquetas de los niveles | `STYLES` |

Si cambia lo que se envía o lo que se guarda en el navegador, hay que revisar
también las [páginas legales](../contenido/paginas-legales.md).
