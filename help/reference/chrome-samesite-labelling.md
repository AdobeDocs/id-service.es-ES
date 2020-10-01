---
title: Cambios en el etiquetado del mismo sitio de Google Chrome
seo-title: Cambios en el etiquetado del mismo sitio de Google Chrome
description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
seo-description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
translation-type: tm+mt
source-git-commit: f74a028532e95ab17f5d2e64697d69eb64e03391
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Cambios en el etiquetado del mismo sitio de Google Chrome {#google-chrome-samesite-labelling-changes}

El atributo SameSite indica a los exploradores cuándo y cómo activar las cookies en los escenarios de origen y de terceros. El atributo SameSite puede tener uno de los tres valores: `strict`, `lax`, o `none`. Chrome, Firefox, Edge, Safari y Opera son compatibles `strict` y `lax` desde noviembre de 2017, mientras que `none` se introdujo en 2018. Sin embargo, algunos exploradores más antiguos no admiten esta configuración.

En febrero de 2020, Google lanzó Chrome 80 y cambió la configuración predeterminada de `none` a `lax` cuando una cookie no tiene un valor de atributo SameSite especificado. Esta configuración evita que una cookie se utilice en un contexto de terceros, también conocido como &quot;entre sitios&quot;. Todas las cookies de terceros posteriores deben configurarse `SameSite=none` y etiquetarse como seguras.

Las cookies sin un valor de atributo SameSite especificado se configurarán de forma predeterminada como `lax`.

Visite el documento [estándar de](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) cookies para obtener más información sobre los atributos del mismo sitio.

## Valores de atributos SameSite

| Valor de atributo SameSite | Descripciones |
| ------ | ------------ |
| `strict` | Las cookies con esta configuración solo se envían cuando la página de referencia y la página de aterrizaje forman parte del mismo dominio que la cookie. |
| `lax` | Las cookies con esta configuración solo se envían cuando el dominio mostrado en la dirección URL del explorador coincide con el dominio de la cookie. Esta es la nueva opción predeterminada para las cookies en Chrome. |
| `none` | Las cookies con esta configuración están disponibles para el acceso externo o de terceros, como &quot;entre sitios&quot;. Antes de este cambio, `none` la configuración predeterminada de SameSite para las cookies era SameSite, por lo que el uso de esta configuración hace que una cookie se comporte de la manera más similar a como ha funcionado tradicionalmente. Sin embargo, Google requiere que cualquier cookie con esta configuración ahora especifique el indicador seguro, lo que significa que la cookie solo se creará y enviará con solicitudes a través de HTTPS. Todas las cookies entre sitios sin el indicador seguro serán rechazadas por Google. |

## Lo que necesita saber como cliente de Adobe Experience Cloud

**No se requieren actualizaciones de JavaScript**

Los productos de Adobe ya han lanzado actualizaciones en el servidor para configurar cookies de terceros con los atributos adecuados. Nuestros clientes no necesitan actualizaciones de la biblioteca JavaScript.

**Asegúrese de que los extremos de terceros utilizan HTTPS**

Todos los clientes deben confirmar que la configuración de JavaScript utiliza HTTPS para sus llamadas a los servicios de Adobe. Destinatario, Audience Manager y el servicio de identidad de Experience Cloud (ECID) están redireccionando las llamadas HTTP de terceros a sus respectivos extremos HTTPS, lo que puede aumentar la latencia. Esto significa que no es necesario que cambie la configuración. Los clientes de Analytics deben actualizar sus implementaciones para que utilicen exclusivamente HTTPS, ya que las redirecciones específicas de Analytics pueden provocar la pérdida de datos.

**Las cookies correctamente etiquetadas deben recopilar los datos según lo previsto**

Mientras las cookies estén etiquetadas correctamente, los navegadores no tomarán ninguna acción para bloquearlas. Los consumidores tendrán la opción de bloquear determinados tipos de cookies, pero actualmente, esta opción solo parece ser una opción de inclusión.

**Las cookies de terceros existentes sin las etiquetas actualizadas se ignorarán**

Chrome 80 ignorará las cookies de terceros que se crearon antes de que Chrome 80 empezara a aplicar SameSite=`none` y la configuración de los indicadores seguros si estos indicadores no están presentes.

Muchas de las cookies de terceros de Adobe existentes no tienen estos indicadores y los servidores Edge deberán actualizarlas antes de que los usuarios actualicen a Chrome 80 o se perderán dichas cookies. La actualización de los servidores Edge se produce automáticamente cuando los usuarios visitan cualquier sitio Web donde se utilice la cookie.

La mayoría de los productos de Adobe ya tienen los indicadores adecuados asignados a las cookies. Las excepciones son implementaciones de Analytics que utilizan recopilación de datos de terceros y no usan ECID. Los clientes pueden experimentar un pequeño aumento temporal de nuevos visitantes que de otra manera habrían estado devolviendo visitantes.

**Posible disminución de coincidencia de cookies para socios de mercado y destino (solo Audience Manager)**

Aunque Adobe tiene control sobre la actualización de las cookies, Adobe no puede obligar a los socios a realizar los cambios necesarios. La coincidencia de cookies puede disminuir para los clientes Audience Manager que utilizan socios de destino o socios de mercado que no han realizado estas actualizaciones.

**Cookies de terceros compatibles con Analytics (solo`s_vi`cookies de Analytics)**

Algunas implementaciones de Analytics utilizan un alias CNAME de Analytics para permitir la creación de la `s_vi` cookie en el dominio de ese CNAME. Si el CNAME está en el mismo dominio que el sitio web, se designará como cookie de origen. Sin embargo, si es propietario de varios dominios y utiliza el mismo CNAME para la recopilación de datos en todos los dominios, se designará como una cookie de terceros en esos otros dominios.

Al `lax` convertirse en la nueva configuración predeterminada SameSite en Chrome, el CNAME ya no es visible en otros dominios.

Para dar cabida al cambio, Analytics ahora establece explícitamente el valor SameSite de la `s_vi` cookie en `lax`. Para utilizar esta cookie en un contexto de terceros más sencillo, establezca el valor SameSite en `none`, lo que también significa que siempre debe utilizar HTTPS. Póngase en contacto con el Servicio de atención al cliente para que se cambie el valor de SameSite para sus CNAME seguros.

> [!IMPORTANT] Esta acción no es necesaria para los clientes de Analytics que usan ECID, los clientes que usan un CNAME independiente para cada uno de sus dominios o los clientes que solo usan recopilación de datos de Analytics de terceros.

## Cookies de Visitante estándar de Adobe

En la tabla siguiente solo se enumeran las cookies estándar comunes de visitante. Para obtener más configuraciones de cookies, consulte la documentación específica del producto o comuníquese con el representante de Adobes.

### ECID

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Origen del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable |
| AMCVS_###@AdobeOrg | Origen del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable |
| s_ecid | Origen del lado del servidor | SameSite==`lax` | No establecido |

### Audience Manager

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terceros | `none` | Establecer como seguro |
| Dextp | Terceros | `none` | Establecer como seguro |

### Analytics

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Origen del lado del servidor si se utiliza `CNAME` </li> <li>Terceros si se utiliza 2o7.net u omtrdc.net</li></ul> | <ul><li>`lax` si es de origen</li> <li>`none` si terceros</li></ul> *Los clientes pueden editar la configuración mediante el ticket del Servicio de atención al cliente para dominios de origen* | Configurar, si se utiliza una solicitud `none` y HTTPS |
| s_fid | Origen del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | No establecido |

### Target

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Datos de origen | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | No establecido |

### Ad Cloud

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terceros | `none` *Solo en exploradores basados en Google Chrome y Chrome* | Configurar, si se utiliza una solicitud `none` y HTTPS |
| data_adcloud | Datos de origen | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | No establecido |
| ev_tm | Terceros | `none` *Solo en exploradores basados en Google Chrome y Chrome* | Configurar, si se utiliza una solicitud `none` y HTTPS |

### Bizible

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terceros | `none` | Secure |

### Marketo Munchkin

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Origen del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable para páginas externas |

> !![IMPORTANT] Las cookies de terceros de Adobe están configuradas en el servidor

Para obtener más información, consulte el documento sobre las directivas [SameSite de Google Chrome](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)Site.