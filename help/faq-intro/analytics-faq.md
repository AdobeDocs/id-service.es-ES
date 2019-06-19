---
description: Las preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.
keywords: Servicio de ID
seo-description: Las preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.
seo-title: Preguntas más frecuentes sobre el servicio de ID y Analytics
title: Preguntas más frecuentes sobre el servicio de ID y Analytics
uuid: 35 ed 79 a 9-eccc -4 b 54-8451-606 f 091 c 73 b 7
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Preguntas más frecuentes sobre el servicio de ID y Analytics{#analytics-and-id-service-faqs}

Las preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.

## Servidores de seguimiento {#section-9a2ad7842e364c869e1650480d17f8ef}

**¿Cómo encuentro la información sobre mi servidor de seguimiento?**

Cada fragmento de código de AppMeasurement configurado adecuadamente contiene la información sobre su servidor de seguimiento.

Sin embargo, a veces, los clientes pueden dividir su archivo de Analytics AppMeasurement en archivos independientes. Por ejemplo, algunos clientes pueden colocar las variables de configuración en un archivo, utilizar un segundo archivo para complementos y luego colocar el código AppMeasurement en un tercer archivo. Esto no se recomienda.

Si no puede encontrar la información sobre su servidor de seguimiento, puede que la instancia de Analytics no esté configurada adecuadamente. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) si no puede encontrar la información sobre su servidor de seguimiento.

**¿Qué ocurre si utilizo el servicio de ID y cambio mi servidor de seguimiento?**

Cuando el servicio de ID haya ya identificado a los usuarios, no cambiará nada. Los visitantes preexistentes que no se hayan migrado al servicio de ID y que sigan identificándose con una cookie de Analytics, se eliminarán. La cantidad de usuarios afectada dependerá del tiempo que haya permanecido activo el servicio de ID. Por ejemplo, una implementación en la que el servicio de ID haya estado activo durante una semana puede tener más usuarios preexistentes que una implementación en la que el servicio de ID haya permanecido activo durante seis meses, ya que se habrían migrado los usuarios que hubieran vuelto al sitio.

## Implementación y configuración {#section-6028f55d5b514ae6a631c6a79f42fb89}

**¿Es necesario configurar un CNAME para hacer un seguimiento de los visitantes en los distintos dominios?**

Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en aquellos navegadores que no acepten cookies de terceros (como Safari).

En los navegadores que aceptan cookies de terceros, se establece una cookie en el [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) durante la solicitud de recuperación de un ID de visitante. Esta cookie permite que el servicio de ID de visitante devuelva el mismo ID de visitante de Experience Cloud en todos los dominios que se hayan configurado con el mismo ID de organización. En los navegadores que no aceptan cookies de terceros, se asigna un nuevo ID de visitante de Experience Cloud en cada dominio.

Incluso aunque se configure un CNAME, si el sitio de entrada principal no se visita en primer lugar, los visitantes se identifican de forma distinta en el sitio secundario y en el principal si se usa un navegador que no acepta cookies de terceros.

**¿Por qué el parámetro de Experience Cloud ID (MID) no está presente en la solicitud de Analytics?**

Si el servicio de ID devuelve la información correctamente pero no encuentra el parámetro `MID`, asegúrese de haber actualizado AppMeasurement a una versión compatible.

**¿Puede mi sitio usar un código H y AppMeasurement para JavaScript con el servicio de ID?**

Sí. Siempre y cuando ambos archivos hagan referencia al mismo archivo VisitorAPI.js, se puede usar la combinación de código H y AppMeasurement para JavaScript en el sitio.

No obstante, el código H no es compatible con el código visitorAPI.js versión 1.6 o posterior. Si desea actualizar a visitorAPI.js v 1.6 (o posterior), no podrá seguir utilizando el código H.

**¿Qué es un período de gracia y cómo lo configuro?**

Consulte [el Período de gracia del servicio de ID](../reference/analytics-reference/grace-period.md) y póngase en contacto con el Servicio [de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**¿Por qué necesito migrar a la recopilación de datos en tiempo real (RDC) para utilizar el servicio de ID?**

RDC suma ventajas de rendimiento globales y es indispensable para garantizar que la implementación esté preparada para admitir funciones futuras que mejorarán la red global de características avanzadas de Adobe. Consulte [Requisitos de Analytics: recopilación de datos regionales (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Informes {#section-123cd55a32e54a45a23beb140becfa8f}

**¿Cuáles son algunas posibles causas de discrepancias al utilizar Analytics con el servicio de ID?**

Entre las causas comunes de discrepancias a la hora de usar el servicio de ID encontramos:

* Uso continuado de la cookie s_vi heredada. Esto contribuye a producir discrepancias en la recopilación de datos. 
* Recuento doble de los visitantes cuando estos se desplazan de una encuesta a una ventana emergente.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**¿Qué sucede en Analytics cuando el servicio de ID no puede establecer la cookie AMCV?**

Hay tres posibles escenarios en los que esto repercute en los datos de Analytics para los visitantes nuevos:

1. Un usuario final abandona una página antes de que la cookie AMCV se establezca correctamente (antes de que se agote el intervalo de tiempo de espera de 30 segundos).

   Si un visitante abandona una página antes de que se acabe de cargar, no se enviará la visita de Analytics. Analytics no recibirá los datos de este escenario y consideraría que estos se han perdido debido a un cierre anticipado de la página. Según las pruebas que realizamos, en las que se incluían geografías alejadas, descubrimos que este escenario representaba menos de un 1 % de la cantidad promedio de tráfico. Es importante tener en cuenta que este escenario ocurre en ocasiones incluso sin la presencia del servicio MCID; es un artefacto de la inclusión del código de recopilación de datos de Analytics en la parte inferior de la página.

1. No se ha asignado un servicio de ID ni un ID de Analytics al usuario final durante el segundo intervalo de tiempo espera de 30 segundos debido a la lentitud de las conexiones o a que el navegador no termina de cargarse.

   No se establecería ni el servicio de ID ni el ID de Analytics y se asignaría un ID del lado del cliente al visitante. Si bien esto permite capturar los datos de Analytics, se interrumpirá el perfil del visitante cuando se establezca un ID de Analytics en una página posterior. El ID del lado del cliente tampoco coincidirá con ningún perfil de visitante existente almacenado en Audience Manager o Analytics. Este ID del lado del cliente también se mostrará como dos visitantes diferentes en Analytics en el caso de que se envíen dos dominios separados en el mismo grupo de informes.

1. No se asigna un ID de servicio de ID a un usuario final durante el intervalo de tiempo de espera de 30 segundos, pero se le asigna un ID de seguimiento de Analytics y no se habilita el período de gracia.

   En el escenario 3 se llega al mismo resultado que en el escenario 2, es decir, se utiliza un ID basado en el lado del cliente.

>[!TIP]
>
>Si utiliza las últimas actualizaciones de visitorapi. js y appmeasurement. js con la configuración predeterminada, debe evitar cualquier impacto grave o patente de los tres escenarios más probables anteriores.

>[!MORE_ LIKE_ THIS]
>
>* [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html)

