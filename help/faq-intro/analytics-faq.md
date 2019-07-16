---
description: Preguntas más frecuentes sobre características, funcionalidades y problemas relacionados con el uso de Analytics con el servicio de identidad de Experience Platform.
keywords: Servicio de identidad de la plataforma de experiencia
seo-description: Preguntas más frecuentes sobre características, funcionalidades y problemas relacionados con el uso de Analytics con el servicio de identidad.
seo-title: Preguntas frecuentes sobre el servicio de identidad y Analytics
title: Preguntas frecuentes sobre el servicio de identidad y Analytics
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

Preguntas más frecuentes sobre características, funcionalidades y problemas relacionados con el uso de Analytics con el servicio de identidad.

## Servidores de seguimiento {#section-9a2ad7842e364c869e1650480d17f8ef}

**¿Cómo encuentro la información sobre mi servidor de seguimiento?**

Cada fragmento de código de AppMeasurement configurado adecuadamente contiene la información sobre su servidor de seguimiento.

Sin embargo, a veces, los clientes pueden dividir su archivo de Analytics AppMeasurement en archivos independientes. Por ejemplo, algunos clientes pueden colocar las variables de configuración en un archivo, utilizar un segundo archivo para complementos y luego colocar el código AppMeasurement en un tercer archivo. Esto no se recomienda.

Si no puede encontrar la información sobre su servidor de seguimiento, puede que la instancia de Analytics no esté configurada adecuadamente. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) si no puede encontrar la información sobre su servidor de seguimiento.

**¿Qué sucede si utilizo el servicio de identidad y cambia mi servidor de seguimiento?**

No cambiará nada para los usuarios que ya hayan sido identificados por el servicio de identidad. Los visitantes preexistentes que no se han migrado al servicio de identidad y que sigan identificándose con una cookie de Analytics se eliminarán. La cantidad de usuarios afectados dependerá del tiempo que haya permanecido activo el servicio de identidad. Por ejemplo: una implementación en la que el servicio de identidad ha estado activa durante 1 semana puede tener más usuarios preexistentes que una implementación en la que el servicio de identidad ha estado activo durante 6 meses, ya que los usuarios que regresen al sitio se habrían migrado.

## Implementación y configuración {#section-6028f55d5b514ae6a631c6a79f42fb89}

**¿Es necesario configurar un CNAME para hacer un seguimiento de los visitantes en los distintos dominios?**

Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en aquellos navegadores que no acepten cookies de terceros (como Safari).

En los navegadores que aceptan cookies de terceros, se establece una cookie en el [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) durante la solicitud de recuperación de un ID de visitante. Esta cookie permite que el servicio de identidad devuelva el mismo ID de visitante de Experience Cloud en todos los dominios configurados con el mismo ID de organización. En los navegadores que no aceptan cookies de terceros, se asigna un nuevo ID de visitante de Experience Cloud en cada dominio.

Incluso aunque se configure un CNAME, si el sitio de entrada principal no se visita en primer lugar, los visitantes se identifican de forma distinta en el sitio secundario y en el principal si se usa un navegador que no acepta cookies de terceros.

**¿Por qué el parámetro de Experience Cloud ID (MID) no está presente en la solicitud de Analytics?**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you&#39;ve upgraded to a supported version of AppMeasurement.

**¿Mi sitio puede utilizar el código H y appmeasurement para JavaScript con el servicio de identidad?**

Sí. Siempre y cuando ambos archivos hagan referencia al mismo archivo VisitorAPI.js, se puede usar la combinación de código H y AppMeasurement para JavaScript en el sitio.

No obstante, el código H no es compatible con el código visitorAPI.js versión 1.6 o posterior. Si desea actualizar a visitorAPI.js v 1.6 (o posterior), no podrá seguir utilizando el código H.

**¿Qué es un período de gracia y cómo lo configuro?**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**¿Por qué necesito migrar a la recopilación de datos en tiempo real (RDC) para utilizar el servicio de identidad?**

RDC suma ventajas de rendimiento globales y es indispensable para garantizar que la implementación esté preparada para admitir funciones futuras que mejorarán la red global de características avanzadas de Adobe. Consulte [Requisitos de Analytics: recopilación de datos regionales (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Informes {#section-123cd55a32e54a45a23beb140becfa8f}

**¿Cuáles son algunas posibles causas de discrepancias al usar Analytics con el servicio de identidad?**

Entre las causas habituales de discrepancias al utilizar el servicio de identidad se incluyen las siguientes:

* Uso continuado de la cookie s_vi heredada. Esto contribuye a producir discrepancias en la recopilación de datos.
* Recuento doble de los visitantes cuando estos se desplazan de una encuesta a una ventana emergente.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**¿Qué sucede en Analytics cuando el servicio de identidad no puede establecer la cookie AMCV?**

Hay tres posibles escenarios en los que esto repercute en los datos de Analytics para los visitantes nuevos:

1. Un usuario final abandona una página antes de que la cookie AMCV se establezca correctamente (antes de que se agote el intervalo de tiempo de espera de 30 segundos).

   Si un visitante abandona una página antes de que se acabe de cargar, no se enviará la visita de Analytics. Analytics no recibirá los datos de este escenario y consideraría que estos se han perdido debido a un cierre anticipado de la página. Según las pruebas que realizamos, en las que se incluían geografías alejadas, descubrimos que este escenario representaba menos de un 1 % de la cantidad promedio de tráfico. Es importante tener en cuenta que este escenario ocurre en ocasiones incluso sin la presencia del servicio de identidad; es un artefacto de la inclusión del código de recopilación de datos de Analytics en la parte inferior de la página.

1. A un usuario final no se le asigna un servicio de identidad ni un ID de Analytics dentro de la ventana de tiempo de espera de 30 segundos debido a la lentitud de las conexiones o el navegador «giro».

   Tanto el servicio de identidad como el ID de Analytics no se establecerían y se asignaría un ID de lado del cliente al visitante. Si bien esto permite capturar los datos de Analytics, se interrumpirá el perfil del visitante cuando se establezca un ID de Analytics en una página posterior. El ID del lado del cliente tampoco coincidirá con ningún perfil de visitante existente almacenado en Audience Manager o Analytics. Este ID del lado del cliente también se mostrará como dos visitantes diferentes en Analytics en el caso de que se envíen dos dominios separados en el mismo grupo de informes.

1. A un usuario final no se le asigna un ID de servicio de identidad dentro de la ventana de tiempo de espera de 30 segundos, pero tiene asignado un ID de seguimiento de Analytics estándar y el período de gracia no está habilitado.

   En el escenario 3 se llega al mismo resultado que en el escenario 2, es decir, se utiliza un ID basado en el lado del cliente.

>[!TIP]
>
>El uso de las actualizaciones más recientes para VisitorAPI.js y AppMeasurement.js con la configuración predeterminada, debería impedir que se produjera cualquier repercusión grave o destacable causada por los tres escenarios improbables que se han indicado anteriormente.

>[!MORE_LIKE_THIS]
>
>* [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html)

