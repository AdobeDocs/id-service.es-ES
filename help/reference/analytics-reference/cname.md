---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: CNAME de recopilación de datos y seguimiento entre dominios
title: CNAME de recopilación de datos y seguimiento entre dominios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---


# CNAME de recopilación de datos y seguimiento entre dominios {#data-collection-cnames-and-cross-domain-tracking}

Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en los exploradores que no acepten cookies de terceros (como Safari).

En los exploradores que aceptan cookies de terceros, los servidores de recopilación de datos configuran una cookie durante la solicitud de un ID de visitante. Esta cookie permite que el servicio de ID de visitante devuelva el mismo ID de visitante de Experience Cloud en todos los dominios que se hayan configurado con el mismo ID de organización de Experience Cloud.

En los exploradores que rechazan cookies de terceros, se asigna un nuevo ID de visitante de Experience Cloud para cada dominio.

La cookie demdex.net permite que el servicio de ID de visitante proporcione el mismo nivel de seguimiento entre dominios que la cookie s_vi en Analytics, donde algunos exploradores aceptan la cookie y la usan en los distintos dominios, pero otros no.

## CNAME de recopilación de datos {#section-48fd186d376a48079769d12c4bd9f317}

Si el servidor de recopilación de datos ha establecido la cookie de Analytics, muchos clientes tendrán configurados registros CNAME del servidor de recopilación de datos como parte de una [implementación de cookies de origen](https://docs.adobe.com/content/help/es-ES/core-services/interface/ec-cookies/cookies-first-party.html) a fin de evitar problemas con los exploradores que no admiten cookies de terceros. Este proceso configura el dominio del servidor de recopilación de datos para que coincida con el dominio del sitio web, de modo que la cookie de ID de visitante se establezca como cookie de origen.

Dado que el servicio de ID de visitante establece la cookie de visitante directamente en el dominio del sitio web actual mediante JavaScript, esta configuración ya no es necesaria para establecer cookies de origen.

Los clientes que tengan una sola propiedad web (un único dominio) pueden dejar de utilizar los registros CNAME de recopilación de datos y usar en su lugar el nombre de host predeterminado de recopilación de datos (`omtrdc.net` o `2o7.net`).

Sin embargo, el uso de un CNAME para la recopilación de datos ofrece una ventaja adicional, ya que permite rastrear visitantes entre un dominio de aterrizaje principal y otros dominios en exploradores que no aceptan cookies de terceros. Los clientes que tienen varias propiedades web (varios dominios) pueden beneficiarse de mantener un CNAME de recopilación de datos. En la siguiente sección se explica cómo funciona el seguimiento de visitantes entre dominios.

## Seguimiento cruzado de dominios {#section-78925af798e24917b9abed79de290ad9}

El servicio de ID de visitante utiliza demdex.net como su dominio para rastrear visitantes entre dominios (pero dentro de la misma compañía propietaria) si la configuración de privacidad y explorador del usuario lo permiten.

Un CNAME no proporciona beneficios adicionales entre dominios. Por ejemplo, supongamos que tiene un sitio principal en `mymainsite.com`. Ha configurado el registro CNAME para que señale a su servidor de recopilación de datos seguro: `smetrics.mymainsite.com`.

Cuando un usuario visite `mymainsite.com`, el servidor de recopilación de datos establecerá la cookie del servicio de ID. Esto se debe a que el dominio de este servidor coincide con el del sitio web. En esta situación se habla de usar una cookie en un *contexto propio*, o simplemente una *cookie de origen*.

Si también usa estos mismos servidores de recopilación de datos en otros sitios (por ejemplo, `myothersiteA.com` y `myothersiteB.com`) y un visitante accede a estos sitios posteriormente, la cookie que se estableció durante la visita a `mymainsite.com` se enviará en la solicitud HTTPS al servidor de recopilación de datos (recuerde que los exploradores envían todas las cookies correspondientes a un dominio con todas las solicitudes HTTPS para dicho dominio, incluso si este no coincide con el dominio del sitio web actual). ¡Esto es lo que se conoce como el uso de una cookie en un *contexto de terceros*, o simplemente una *cookie de terceros*, aunque esté utilizando un CNAME. Adobe recomienda un CNAME para cada dominio único.

*Nota: Safari bloquea todas las cookies en el contexto de terceros independientemente de su configuración.*

## Habilitación de la compatibilidad con CNAME con el servicio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Para habilitar la compatibilidad con el CNAME del servidor de recopilación de datos, se deben establecer las `visitor.marketingCloudServerSecure` variables.
