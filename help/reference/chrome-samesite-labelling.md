---
title: Cambios en el etiquetado de SameSite de Google Chrome
description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 100%

---

# Cambios en el etiquetado de SameSite de Google Chrome {#google-chrome-samesite-labelling-changes}

El atributo SameSite indica a los exploradores cuándo y cómo activar las cookies en los escenarios de origen y de terceros. El atributo SameSite puede tener uno de estos tres valores: `strict`, `lax` o `none`. Chrome, Firefox, Edge, Safari y Opera admiten `strict` y `lax` desde noviembre de 2017, mientras que `none` se introdujo en 2018. Sin embargo, algunos exploradores más antiguos no admiten esta configuración.

En febrero de 2020, Google lanzó Chrome 80 y cambió la configuración predeterminada de `none` a `lax` cuando una cookie no tiene un valor de atributo SameSite especificado. Esta configuración evita que una cookie se utilice en un contexto de terceros, también conocido como “entre sitios”. Todas las cookies de terceros posteriores deben configurarse como `SameSite=none` y etiquetarse como seguras.

Las cookies sin un valor de atributo SameSite especificado se configurarán de forma predeterminada como `lax`.

Visite el [documento de estándares de cookies](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) para obtener más información sobre los atributos SameSite.

## Valores de atributos SameSite

| Valor de atributo SameSite | Descripciones |
| ------ | ------------ |
| `strict` | Las cookies con esta configuración solo se envían cuando la página de referencia y la página de aterrizaje forman parte del mismo dominio que la cookie. |
| `lax` | Las cookies con esta configuración solo se envían cuando el dominio mostrado en la dirección URL del explorador coincide con el dominio de la cookie. Esta es la nueva opción predeterminada para las cookies en Chrome. |
| `none` | Las cookies con esta configuración están disponibles para el acceso externo o de terceros, como “entre sitios”. Antes de este cambio, `none` era la configuración predeterminada de SameSite para las cookies, por lo que el uso de esta configuración hace que una cookie se comporte de la manera más similar a como ha funcionado tradicionalmente. Sin embargo, Google requiere que cualquier cookie con esta configuración ahora especifique el indicador seguro, lo que significa que la cookie solo se creará y enviará con solicitudes a través de HTTPS. Todas las cookies entre sitios sin el indicador seguro serán rechazadas por Google. |

## Lo que necesita saber como cliente de Adobe Experience Cloud

**No se requieren actualizaciones de JavaScript**

Los productos de Adobe ya han publicado actualizaciones del lado del servidor para establecer las cookies de terceros con los atributos adecuados. Nuestros clientes no necesitan actualizaciones de la biblioteca JavaScript.

**Asegúrese de que los puntos de conexión de terceros utilizan HTTPS**

Todos los clientes de Analytics deben confirmar que su configuración de JavaScript utiliza HTTPS para sus llamadas a los servicios de Adobe. Target, Audience Manager y el servicio de ID de Experience Cloud (ECID) están redireccionando las llamadas HTTP de terceros a sus respectivos puntos de conexión HTTPS, lo que puede aumentar la latencia. Esto significa que no es necesario que cambie la configuración. Los clientes de Analytics deben actualizar sus implementaciones para que utilicen exclusivamente HTTPS, ya que las redirecciones específicas de Analytics pueden provocar la pérdida de datos.

**Las cookies correctamente etiquetadas deben recopilar los datos según lo previsto**

Mientras las cookies estén etiquetadas correctamente, los navegadores no tomarán ninguna acción para bloquearlas. Los consumidores tendrán la opción de bloquear determinados tipos de cookies, pero actualmente, esta parece ser una opción de inclusión.

**Las cookies de terceros existentes sin las etiquetas actualizadas se ignorarán**

Chrome 80 ignorará las cookies de terceros que se crearon antes de que Chrome 80 empezara a aplicar SameSite=`none` y la configuración de los indicadores seguros si estos indicadores no están presentes.

Muchas de las cookies de terceros de Adobe existentes no tienen estos indicadores y los servidores Edge deberán actualizarlas antes de que los usuarios actualicen a Chrome 80 o se perderán dichas cookies. La actualización de los servidores Edge se produce automáticamente cuando los usuarios visitan cualquier sitio web donde se utilice la cookie.

La mayoría de los productos de Adobe ya tienen los indicadores adecuados asignados a las cookies. Las excepciones son implementaciones de Analytics que utilizan recopilación de datos de terceros y no usan un ECID. Es posible que los clientes experimenten un pequeño aumento temporal de nuevos visitantes que, de lo contrario, se habrían clasificado como visitantes que retornan.

**Posible disminución de coincidencia de cookies para socios de mercado y destino (solo Audience Manager)**

Aunque Adobe tiene control sobre la actualización de las cookies, Adobe no puede obligar a los socios a realizar los cambios necesarios. La coincidencia de cookies puede disminuir para los clientes de Audience Manager que colaboren con socios de destino o socios de mercado que no han realizado estas actualizaciones.

**Cookies de terceros compatibles con Analytics (solo `s_vi` cookies de Analytics)**

Algunas implementaciones de Analytics utilizan un alias CNAME de Analytics para permitir la creación de la cookie `s_vi` en el dominio de ese CNAME. Si el CNAME está en el mismo dominio que el sitio web, se designará como cookie de origen. Sin embargo, si es propietario de varios dominios y utiliza el mismo CNAME para la recopilación de datos en todos los dominios, este designa como una cookie de terceros en esos otros dominios.

Una vez que `lax` se convierta en la nueva configuración predeterminada de SameSite en Chrome, el CNAME ya no será visible en otros dominios.

Para dar cabida al cambio, Analytics ahora establece explícitamente el valor SameSite de la cookie `s_vi` como `lax`. Para utilizar esta cookie en un contexto de terceros más sencillo, establezca el valor SameSite en `none`, lo que también significa que siempre debe utilizar HTTPS. Contacte con el Servicio de atención al cliente de para que se cambie el valor de SameSite para sus CNAME seguros.

>[!IMPORTANT]
>
>Esta acción no es necesaria para los clientes de Analytics que usan ECID, los clientes que usan un CNAME independiente para cada uno de sus dominios o los clientes que solo usan recopilación de datos de Analytics de terceros.

## Cookies de visitante estándar de Adobe

En la tabla siguiente solo se enumeran las cookies estándar comunes de visitantes. Para obtener más configuraciones de cookies, consulte la documentación específica del producto o contacte con el representante de Adobe.

### ECID

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Origen del lado del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable |
| AMCVS_###@AdobeOrg | Origen del lado del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable |
| s_ecid | Origen del lado del servidor | SameSite==`lax` | Sin configurar |

### Audience Manager

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terceros | `none` | Configurado como seguro |
| Dextp | Terceros | `none` | Configurado como seguro |

### Analytics

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Origen del lado del servidor si se utiliza un `CNAME` </li> <li>Terceros si se utiliza 2o7.net u omtrdc.net</li></ul> | <ul><li>`lax` si es de origen</li> <li>`none` si es de terceros</li></ul> *Los clientes pueden editar la configuración mediante el ticket del Servicio de atención al cliente para dominios de origen* | Se debe configurar, si se utiliza `none` y una solicitud HTTPS |
| s_fid | Origen del lado del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Sin configurar |

### Target

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Datos de origen | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Sin configurar |

### Ad Cloud

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terceros | `none` *Solo en exploradores Google Chrome y basados en Chromium* | Se debe configurar, si se utiliza `none` y una solicitud HTTPS |
| data_adcloud | Datos de origen | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Sin configurar |
| ev_tm | Terceros | `none` *Solo en exploradores Google Chrome y basados en Chromium* | Se debe configurar, si se utiliza `none` y una solicitud HTTPS |

### Bizible

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terceros | `none` | Secure |

### Marketo Munchkin

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Origen del lado del cliente | No se ha agregado ningún valor *Chrome establece de forma predeterminada `lax` | Configurable para páginas externas |

> !![IMPORTANT] Las cookies de terceros de Adobe se configuran del lado del servidor

Para obtener más información, consulte el documento sobre [directivas de Target sobre SameSite de Google Chrome](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html?lang=es).
