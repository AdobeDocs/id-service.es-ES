---
description: 'null'
keywords: orden de las operaciones; Servicio de ID
seo-description: 'null'
seo-title: CNAME de recopilación de datos y seguimiento entre dominios
title: CNAME de recopilación de datos y seguimiento entre dominios
uuid: ba 42 c 822-b 677-4139-b 1 ed -4 d 98 d 3320 fd 0
translation-type: tm+mt
source-git-commit: 337e7eef2cce8c0bc827ec04833ad0d14ee9c89a

---


# CNAME de recopilación de datos y seguimiento entre dominios{#data-collection-cnames-and-cross-domain-tracking}

Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en aquellos navegadores que no acepten cookies de terceros (como Safari).

En los exploradores que aceptan cookies de terceros, los servidores de recopilación de datos establecen las cookies durante la solicitud de un ID de visitante. Esta cookie permite que el servicio de ID de visitante devuelva el mismo ID de visitante de Experience Cloud en todos los dominios que se hayan configurado con el mismo ID de organización de Experience Cloud.

En los navegadores que no aceptan cookies de terceros, se asigna un nuevo ID de visitante de Experience Cloud en cada dominio.

La cookie demdex.net permite que el servicio de ID de visitante proporcione el mismo nivel de seguimiento entre dominios que la cookie s_vi en Analytics, donde algunos exploradores aceptan la cookie y la usan en los distintos dominios, pero otros no.

## CNAME de recopilación de datos {#section-48fd186d376a48079769d12c4bd9f317}

Si el servidor de recopilación de datos ha establecido la cookie de Analytics, muchos clientes tendrán configurados registros CNAME del servidor de recopilación de datos como parte de una [implementación de cookies de origen](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) a fin de evitar problemas con los exploradores que no admiten cookies de terceros. Este proceso configura el dominio del servidor de recopilación de datos para que coincida con el dominio de su sitio web, de forma que la cookie del ID de visitante se establezca como cookie de origen.

Como el servicio de ID de visitante establece la cookie del visitante directamente en el dominio del sitio web actual mediante JavaScript, ya no es necesario realizar esta configuración para establecer las cookies de origen.

Los clientes que tengan una sola propiedad web (un único dominio) pueden dejar de utilizar los registros CNAME de recopilación de datos y usar en su lugar el nombre de host predeterminado de recopilación de datos (`omtrdc.net` `2o7.net`o).

No obstante, el uso de un registro CNAME para la recopilación de datos ofrece una ventaja adicional, ya que permite hacer un seguimiento de los visitantes entre un dominio de aterrizaje principal y otros dominios en aquellos exploradores que no acepten cookies de terceros. Los clientes que tienen varias propiedades web (varios dominios) pueden encontrar útil mantener un CNAME de recopilación de datos. En la sección siguiente se explica cómo funciona el seguimiento de visitantes entre dominios.

## Cómo habilitan los registros CNAME el seguimiento entre dominios {#section-78925af798e24917b9abed79de290ad9}

Gracias al modo en que las cookies de origen pueden utilizarse en un contexto de terceros en Apple Safari y otros exploradores, un registro CNAME le permite hacer un seguimiento de los visitantes entre un dominio principal y otros dominios adicionales que hayan utilizado el mismo servidor de seguimiento.

Por ejemplo, supongamos que tiene un sitio principal en `mymainsite.com` Ha configurado el registro CNAME para que señale a su servidor de recopilación de datos seguro: `smetrics.mymainsite.com`.

Cuando un usuario visite `mymainsite.com`, el servidor de recopilación de datos establecerá la cookie del servicio de ID. Esto se permite porque el dominio del servidor de recopilación de datos coincide con el dominio del sitio web, y es lo que se conoce como usar una cookie en un contexto **de origen o solo una cookie *de origen*.

Si también utiliza este mismo servidor de recopilación de datos en otros sitios (por ejemplo, `myothersiteA.com`y `myothersiteB.com`) y un visitante visita más tarde estos sitios, la cookie que se configuró durante la visita a `mymainsite.com` se envía en la solicitud HTTPS al servidor de recopilación de datos (recuerde que los exploradores envían todas las cookies de un dominio con todas las solicitudes HTTPS a ese dominio, incluso aunque el dominio no coincide con el dominio del sitio web actual). Esto es lo que se conoce como uso de una cookie en un contexto **de terceros o solo una cookie **de terceros y permite utilizar el mismo ID de visitante en estos otros dominios. Tenga en cuenta que los navegadores administran cookies en contextos de terceros de manera diferente a las cookies de origen.

*Nota: Safari bloquea todas las cookies en el contexto de terceros independientemente de su configuración.*

En consecuencia, el dominio de recopilación debe ser un dominio al que los visitantes accedan con frecuencia para posibilitar la identificación de estos en los distintos dominios. Si no hay dominio *común* que utilizar para el dominio de recopilación de datos, no hay ninguna ventaja entre dominios para mantener un CNAME para el dominio de recopilación de datos. Si el sitio de entrada principal no se visita en primer lugar, los visitantes se identifican de forma distinta en el sitio secundario y en el sitio principal.

## Habilitación de la compatibilidad con CNAME con el servicio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La compatibilidad con CNAME de servidor de recopilación de datos se habilita al configurar `visitor.marketingCloudServerSecure` las variables.
