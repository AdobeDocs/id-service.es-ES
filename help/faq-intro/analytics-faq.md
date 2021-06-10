---
description: Las preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de identidad de Experience Cloud.
keywords: Servicio de Experience Cloud ID
title: Preguntas frecuentes sobre el servicio de ID y Analytics
exl-id: 98aeca0d-41a2-4b18-b307-19a6de816e38
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 99%

---

# Preguntas frecuentes sobre el servicio de ID y Analytics {#analytics-and-id-service-faqs}

Preguntas frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.

## Servidores de seguimiento {#section-9a2ad7842e364c869e1650480d17f8ef}

**¿Cómo encuentro la información del servidor de seguimiento?**

Cada parte del código de AppMeasurement configurada correctamente contiene la información del servidor de seguimiento.

Sin embargo, a veces los clientes pueden dividir su archivo de AppMeasurement de Analytics en archivos independientes. Por ejemplo, algunos clientes pueden colocar variables de configuración en un archivo, utilizar un segundo archivo para complementos y luego colocar el código de AppMeasurement en un tercer archivo. Este proceso no es recomendable.

Si no encuentra la información del servidor de seguimiento, es posible que la instancia de Analytics no esté configurada correctamente. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) si no encuentra la información del servidor de seguimiento.

**¿Qué ocurre si utilizo el servicio de identidad y cambio mi servidor de seguimiento?**

Cuando el servicio de identidad haya identificado a los usuarios, no cambiará nada. Los visitantes históricos que no se hayan migrado al servicio de identidad y que sigan identificándose con una cookie de Analytics se eliminarán. La cantidad de usuarios afectada dependerá del tiempo que haya permanecido activo el servicio de identidad. Por ejemplo, una implementación en la que el servicio de identidad haya estado activo durante una semana puede tener más usuarios históricos que una implementación en la que el servicio de identidad haya permanecido activo durante seis meses, ya que se habrían migrado los usuarios que volvieron al sitio.

## Implementación y configuración {#section-6028f55d5b514ae6a631c6a79f42fb89}

**¿Tengo que configurar un CNAME para rastrear visitantes entre dominios?**

Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en los exploradores que no acepten cookies de terceros (como Safari).

En los exploradores que aceptan cookies de terceros, se establece una cookie en el [dominio demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html) durante la solicitud para recuperar un ID de visitante. Esta cookie permite que el servicio de identidad de visitante devuelva el mismo ID de visitante de Experience Cloud en todos los dominios que se hayan configurado con el mismo ID de organización. En los exploradores que rechazan cookies de terceros, se asigna un nuevo ID de visitante de Experience Cloud para cada dominio.

Incluso cuando se configura un CNAME, si el sitio de entrada principal no se visita primero, los visitantes se identifican de forma diferente en el sitio secundario y en el principal en los exploradores que no aceptan cookies de terceros.

**¿Por qué el parámetro de Experience Cloud ID (MID) no está presente en la solicitud de Analytics?**

Si el servicio de identidad devuelve la información correctamente pero no encuentra el `MID` parámetro, asegúrese de haber actualizado AppMeasurement a una versión compatible.

**¿Puede mi sitio usar un código H y AppMeasurement para JavaScript con el servicio de identidad?**

Sí. Siempre que ambos archivos hagan referencia al mismo archivo VisitorAPI.js, se puede utilizar una combinación de código H y AppMeasurement para JavaScript en el sitio.

Sin embargo, el código H no es compatible con el código visitorAPI.js 1.6 o posterior. Si desea actualizar a visitorAPI.js 1.6 (o posterior), no podrá seguir utilizando el código H.

**¿Qué es un periodo de gracia y cómo puedo configurarlo?**

Consulte [Período de gracia de servicio de identidad](../reference/analytics-reference/grace-period.md) y póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**¿Por qué necesito migrar a la recopilación de datos en tiempo real (RDC) para utilizar el servicio de identidad?**

La RDC mejora el rendimiento general y es necesaria para asegurarse de que la implementación está lista para las próximas funciones que aprovechan la red global de notas avanzadas de Adobe. Consulte [Requisitos de Analytics: Recopilación de datos regionales (RDC). ](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)

## Informes {#section-123cd55a32e54a45a23beb140becfa8f}

**¿Cuáles son algunas posibles causas de discrepancias al utilizar Analytics con el servicio de identidad?**

Entre las causas comunes de discrepancias a la hora de usar el servicio de identidad encontramos:

* Uso continuo de la cookie s_vi heredada. Esto contribuye a producir discrepancias en la recopilación de datos.
* Recuento doble de los visitantes cuando navegan desde una encuesta a una ventana emergente.

## Cookies  {#section-b7d5384fbedd47b09e1030211c39a3d1}

**¿Qué sucede en Analytics cuando el servicio de identidad no puede establecer la cookie AMCV?**

Hay tres escenarios posibles en los que esto afecta a los datos de Analytics para nuevos visitantes:

1. Un usuario final abandona una página antes de que las cookies AMCV se configuren correctamente (dentro del tiempo de espera de 30 segundos).

   Si un visitante abandona una página antes de que termine de cargarse, la visita de Analytics no se envía. Analytics no recibirá datos de este escenario y considerará que los datos se han perdido debido al cierre anticipado de la página. Basándonos en nuestras pruebas, que incluían ubicaciones alejadas entre sí, descubrimos que este escenario representaba menos del 1% del tráfico en promedio. Es importante indicar que este escenario se produce, a veces, incluso sin la presencia del servicio MCID; se trata de un efecto visual por la inclusión del código de recopilación de datos de Analytics que aparece en la parte inferior de la página.

1. No se ha asignado un servicio de identidad ni un ID de Analytics al usuario final durante el segundo intervalo de tiempo espera de 30 segundos debido a la lentitud de las conexiones o a que el navegador no termina de cargarse.

   No se establecería ni el servicio de identidad ni el ID de Analytics y se asignaría un ID del lado del cliente al visitante. Aunque esto permite recopilar datos de Analytics, el perfil del visitante se interrumpirá cuando se establezca un ID de Analytics en una página posterior. El ID del lado del cliente tampoco coincidirá con ningún perfil de visitante existente almacenado en Audience Manager o Analytics. Este ID del lado del cliente también aparecerá como dos visitantes diferentes en Analytics si se envían dos dominios independientes al mismo grupo de informes.

1. No se asigna un ID de servicio de identidad a un usuario final durante el intervalo de tiempo de espera de 30 segundos, pero se le asigna un ID de seguimiento de Analytics y no se habilita el período de gracia.

   En el escenario 3 se llega al mismo resultado que en el escenario 2, es decir, se utiliza un ID basado en el lado del cliente.

>[!TIP]
>
>El uso de las actualizaciones más recientes para VisitorAPI.js y AppMeasurement.js con la configuración predeterminada, debería impedir que se produjera cualquier repercusión grave o destacable causada por los tres escenarios improbables que se han indicado anteriormente.

>[!MORELIKETHIS]
>
>* [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html)

