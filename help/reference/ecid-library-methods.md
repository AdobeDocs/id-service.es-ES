---
title: Métodos de biblioteca ECID en un entorno de Safari ITP
seo-title: Métodos de biblioteca ECID en un entorno de Safari ITP
description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
seo-description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
translation-type: ht
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: ht
source-wordcount: '1090'
ht-degree: 100%

---


# Métodos de biblioteca ECID en un entorno de Safari ITP

A medida que Safari aumenta el seguimiento entre dominios a través de ITP, Adobe debe mantener las prácticas recomendadas para bibliotecas que sean compatibles con los clientes, así como con la privacidad y con la opción del consumidor.

El 21 de febrero de 2019, Apple anunció su última actualización de ITP (Prevención inteligente de seguimiento). A diferencia de las versiones anteriores centradas en cookies de terceros, esta versión detalla nuevas medidas preventivas para el seguimiento de cookies propias. Todas las cookies persistentes propias configuradas a través de la API document.cookie, generalmente conocidas como “cookies del lado del cliente”, caducan a los 7 días. Las cookies de terceros se seguirán bloqueando, tal como se indica en versiones anteriores de ITP. Para obtener más información sobre ITP 2.1 y el impacto de las soluciones de Adobe, lea sobre [el impacto de Safari ITP 2.1 en Adobe Experience Cloud y en la plataforma de Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Preguntas frecuentes sobre Adobe ECID para Safari ITP

**¿Por qué la cookie AMCV, establecida por la biblioteca de Experience Cloud ID (ECID) afecta a ITP 2.1 en un dominio propio de los clientes?**

Actualmente, la cookie AMCV se basa en la API document.cookie y se configura con un proceso “del lado del cliente”. Safari prefiere las cookies configuradas desde el servidor de un cliente.

**¿Por qué una cookie establecida mediante un servidor de seguimiento CNAME es una mejor opción para realizar el seguimiento en Safari?**

Las reglas de ITP se centran en devolver el control a los desarrolladores. Las implementaciones a través de certificados CNAME no se pueden realizar con solo JavaScript. El programa de certificación CNAME de Adobe (seguimiento del lado del servidor) está sincronizado con ITP y forma parte de la estrategia de Adobe desde hace muchos años. La biblioteca ECID es un método que se centra en mover la funcionalidad de biblioteca ECID a una implementación CNAME.

**¿Por qué Adobe se centra en la biblioteca ECID cuando hoy en día se utilizan otros métodos de seguimiento de visitantes de Analytics con CNAME?**

La biblioteca ECID, la cookie AMCV y ECID (también llamado MID) comenzaron como un método para integrar todas las soluciones de Adobe en un único ID. Este ID seguirá siendo el ID de nivel de cookie prioritario en la hoja de ruta de productos de Adobe, y es el ID de cookie predeterminado para Adobe Experience Platform.

**¿CNAME ayuda a los clientes a habilitar el seguimiento de dominios múltiples?**

Las mismas reglas y advertencias que existían anteriormente con CNAME todavía existen. En algunos casos, los CNAME pueden ayudar en un escenario de dominios múltiples. Si tiene un sitio de entrada principal en el que se puede identificar a los usuarios antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento de dominios múltiples en los navegadores que no acepten cookies de terceros. Sin embargo, aunque los CNAME pueden ayudar con los dominios múltiples en algunos casos, la razón de la transferencia de ECID a las implementaciones CNAME es la identificación persistente de visitantes, no el seguimiento de dominios múltiples. Para obtener más información sobre CNAME y los dominios múltiples, consulte [CNAME de recopilación de datos y seguimiento entre dominios](/help/reference/analytics-reference/cname.md).

Se agregarán más preguntas frecuentes aquí a medida que se realicen cambios de ITP adicionales. Para obtener más información, visite [Adobe Experience League](https://experienceleague.adobe.com/?lang=es#recommended/solutions/analytics).

## Cambios, métodos y configuraciones relacionados con ITP

A medida que se crean métodos adicionales para el seguimiento dentro de Safari, se agregarán como referencia a esta página.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* en toda la documentación siguiente.

Consulte más abajo las iniciativas relacionadas con el uso de bibliotecas de ITP y ECID.

## Utilice la biblioteca ECID y el seguimiento CNAME para ampliar la caducidad del ID de visitante

ITP 2.1 impide escribir cookies del lado del cliente, lo cual reduce la capacidad de proporcionar información exacta del seguimiento de visitantes a los clientes. Por esta razón, se está introduciendo un cambio en los servidores de seguimiento CNAME de Adobe para almacenar el Experience Cloud ID (ECID) del visitante en una cookie propia.

Este cambio solo es útil para clientes ECID que utilizan un CNAME de Analytics en un contexto propio. Si es cliente de Analytics que actualmente no utiliza un CNAME, o incluso un cliente que no sea de Analytics, podrá optar por un registro CNAME. Póngase en contacto con el Servicio de atención al cliente o con su representante de cuentas para iniciar el proceso de registro para un [CNAME](https://docs.adobe.com/content/help/es-ES/core-services/interface/ec-cookies/cookies-first-party.html).

Actualice a la biblioteca ECID versión 4.3.0 (o posterior) para aprovechar este cambio.

**Diseño**

Cuando se realiza una solicitud de ID a demdex.net y se recupera un ECID, si se configura un servidor de seguimiento en la biblioteca ECID, se realiza una solicitud de ID al dominio del cliente. Este extremo lee el parámetro ecid de la cadena de consulta y establece una nueva [cookie](/help/introduction/cookies.md) que incluye solo el ECID y una fecha de caducidad para dentro de dos años. Cada vez que se llama este extremo de esta manera, la cookie `s_ecid` se reescribe con una fecha de caducidad de dos años desde la hora de la llamada. La biblioteca ECID debe actualizarse a la versión 4.3.0 para poder recuperar el valor de esta cookie.

Esta nueva cookie `s_ecid` sigue el mismo estado de exclusión que la cookie AMCV. Si se lee el ecid de la cookie `s_ecid`, siempre se llama inmediatamente a demdex para recuperar el estado de exclusión más reciente de ese ID y se almacena en la cookie AMCV.

Además, si el consumidor se ha excluido del seguimiento de Analytics mediante este [método](https://docs.adobe.com/content/help/es-ES/analytics/implementation/js/opt-out.html), se eliminará esta cookie `s_ecid`.

El nombre del servidor de seguimiento debe proporcionarse a la biblioteca VisitorJS al inicializar la biblioteca mediante trackingServer o trackingServerSecure. Debe coincidir con la configuración trackingServer en las configuraciones de Analytics.

Si decide no aprovechar este método, agregue la siguiente configuración a su implementación de biblioteca ECID: discardtrackingServerECID. Cuando esta configuración se establece en “true”, la biblioteca de visitante no lee el MID configurado por el servidor de seguimiento propio.

![](assets/itp-proposal-v1.png)

## Utilice el método appendVisitorIDsTo para el seguimiento entre dominios (dentro de los múltiples dominios de la empresa)

Esta función le permite compartir un ECID de un visitante entre dominios cuando los navegadores bloquean las cookies de terceros. Para utilizar esta función, debe haber implementado el servicio de ID y ser el propietario de los dominios de origen y destino. Disponible en VisitorAPI.js en la versión 1.7.0 o superior (pero no en la versión 1.10.0).

**Diseño**

* Cuando un visitante navega a sus otros dominios, Visitor.appendVisitorIDsTo(url) devuelve una URL con ECID adjunta como parámetro de consulta.

   Utilice esta URL para redireccionar desde el dominio original al dominio de destino.

* Este código de servicio de ID en el dominio de destino extrae el ECID de la URL, en lugar de enviar una solicitud a Adobe para obtener el ID del visitante en cuestión.

   Esta solicitud incluye el ID de la cookie de terceros, que no está disponible en este caso.

* El código de servicio de ID en la página de destino emplea el ECID transferido para hacer un seguimiento del visitante.

   >[!NOTE]
   >Si la página de destino ya tiene un ECID de visitas anteriores, la decisión de sobrescribir la cookie existente está controlada por esta configuración overwriteCrossDomainMCIDAndAID. Para obtener más información sobre esta configuración, consulte [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Para obtener más detalles sobre este método, consulte la página de referencia [appendVisitorIDsTo (Seguimiento entre dominios)](/help/library/get-set/appendvisitorid.md).
