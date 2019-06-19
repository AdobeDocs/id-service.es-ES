---
title: Métodos de biblioteca ECID en un mundo Safari ITP
seo-title: Métodos de biblioteca ECID en un mundo Safari ITP
description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
seo-description: Documentación para la biblioteca de Adobe ECID (servicio de ID).
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Métodos de biblioteca ECID en un mundo Safari ITP

A medida que Safari aumenta el seguimiento entre dominios a través de ITP, Adobe debe mantener las prácticas recomendadas para bibliotecas que admitan clientes como así también la privacidad y opción del consumidor.

El 21 de febrero de 2019, Apple anunció su última actualización de ITP (Prevención inteligente de seguimiento). A diferencia de las versiones anteriores centradas en cookies de terceros, esta versión detalla nuevas medidas de prevención de seguimiento para cookies individuales. Todas las cookies persistentes individuales configuradas a través de la API document. cookie, generalmente conocidas como cookies del lado del cliente, tienen su caducidad a los 7 días. Las cookies de terceros se seguirán bloqueando, tal como se indica en versiones anteriores de ITP. Para obtener más información sobre ITP 2.1 y el impacto de las soluciones de Adobe, lea [el impacto de Safari ITP 2.1 en Adobe Experience Cloud y clientes de Experience Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Adobe ECID para preguntas más frecuentes sobre Safari ITP

**¿Por qué la cookie AMCV, establecida por la biblioteca de ID de Experience Cloud (ECID) en un dominio de origen de los clientes, afecta a ITP 2.1?**

Actualmente, la cookie AMCV se basa en la API document. cookie y se configura mediante &quot;lado del cliente&quot;. Safari favorece las cookies configuradas desde el servidor de un cliente.

**¿Por qué se establece una cookie mediante un servidor de seguimiento CNAME una mejor opción para realizar el seguimiento en Safari?**

Las reglas de ITP se centran en devolver el control a los desarrolladores. Las implementaciones a través de certificados CNAME no se pueden realizar por solo JavaScript. El programa de certificación CNAME de Adobe (seguimiento del lado del servidor) está en línea con ITP y forma parte de la estrategia de Adobe durante muchos años. La biblioteca ECID es un método que se centra en mover la funcionalidad de biblioteca ECID a una implementación CNAME.

**¿Por qué se centra Adobe en la biblioteca ECID cuando se utilizan otros métodos de seguimiento de visitantes de Analytics con CNAME hoy?**

La biblioteca ECID, la cookie AMCV y ECID (MID) comenzaron como método para integrar todas las soluciones de Adobe en un único ID. Este ID seguirá siendo la ID de nivel de cookie prioritaria en la hoja de ruta de productos de Adobe y es el ID de cookie predeterminado para Adobe Experience Platform.

**¿Cname ayuda a los clientes a habilitar el seguimiento de múltiples dominios?**

Las mismas reglas y advertencias que existían anteriormente con CNAME todavía existen. En algunos casos, los CNAME pueden ayudar en un escenario de varios dominios. Si tiene un sitio de entrada principal donde los usuarios se pueden identificar antes de visitar otros dominios, un CNAME puede habilitar el seguimiento de múltiples dominios en los exploradores que no aceptan cookies de terceros. Sin embargo, aunque cnames puede ayudar con varios dominios en algunos escenarios, la razón de la transferencia de ECID a las implementaciones CNAME es la identificación persistente de visitantes, no el seguimiento de múltiples dominios. Para obtener más información sobre CNAME y multidominio, consulte [CNAME de recopilación de datos y seguimiento entre dominios](/help/reference/analytics-reference/cname.md).

Se agregarán más preguntas más frecuentes aquí a medida que se lanzan cambios de ITP adicionales. Para obtener más consultas, visite [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Cambios, métodos y configuraciones relacionados con ITP

A medida que se crean métodos adicionales para el seguimiento dentro de Safari, se agregarán como referencia a esta página.

>[!NOTE]*ECID* = *MID* = *MCID* en toda la documentación siguiente.

Consulte más abajo los esfuerzos relacionados con el uso de bibliotecas de ITP y ECID.

## Utilice la biblioteca ECID y el seguimiento CNAME para ampliar la caducidad del ID de visitante

ITP 2.1 desactiva la capacidad de escribir cookies del lado del cliente, lo cual afecta a la capacidad de proporcionar información exacta del seguimiento de visitantes a los clientes. Como tal, se está introduciendo un cambio en los servidores de seguimiento CNAME de Adobe para almacenar el ID de Experience Cloud (ECID) del visitante en una cookie de origen.

Este cambio solo es útil para clientes ECID que utilizan un CNAME de Analytics en contexto de origen. Si es cliente de Analytics que actualmente no utiliza un CNAME, o incluso un cliente que no sea de Analytics, podrá optar a un registro CNAME. Póngase en contacto con el Servicio de atención al cliente o con su representante de cuentas para iniciar el proceso de registro para un [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Actualice a la biblioteca ECID v. 4.3.0 + para aprovechar este cambio.

**Diseño**

Cuando se realiza una solicitud de ID a demdex. net y se recupera un ECID, si se configura un servidor de seguimiento en la biblioteca ECID, se realiza una solicitud de ID al dominio del cliente. Este extremo lee el parámetro ecid de la cadena de consultas y establece una nueva [cookie](/help/introduction/cookies.md) que incluye sólo el ECID y una fecha de caducidad dos años más adelante. Cada vez que se llama este extremo de esta manera, la `s_ecid` cookie se vuelve a escribir con una fecha de caducidad de dos años desde la hora de la llamada. La biblioteca ECID debe actualizarse a v 4.3.0 para poder recuperar el valor de esta cookie.

Esta nueva `s_ecid` cookie sigue el mismo estado de exclusión que la cookie AMCV. Si se lee el ecid de la `s_ecid` cookie, siempre se llama inmediatamente a demdex para recuperar el estado de exclusión más reciente de ese ID y almacenarse en la cookie AMCV.

Además, si el consumidor ha excluido el seguimiento de Analytics mediante este [método](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), se eliminará esta `s_ecid` cookie.

El nombre del servidor de seguimiento debe proporcionarse a la biblioteca visitorjs al inicializar la biblioteca mediante trackingserver o trackingserversecure. Debe coincidir con la configuración trackingserver en las configuraciones de Analytics.

Si decide no aprovechar este método, agregue la siguiente configuración a su implementación de biblioteca ECID: Discardtrackingserverecid. Cuando esta configuración se establece en true, la biblioteca de visitante no lee el MID configurado por el servidor de seguimiento de origen.

![](assets/itp-proposal-v1.png)

## Utilizar el método appendvisitoridsto para el seguimiento entre dominios (dentro de los múltiples dominios de la empresa)

Esta función permite compartir el ECID de un visitante entre dominios cuando los exploradores bloquean cookies de terceros. Para utilizar esta función, debe haber implementado el servicio de ID y ser el propietario de los dominios de origen y destino. Disponible en visitorapi. js versión 1.7.0 o superior (pero no en la versión 1.10.0).

**Diseño**

* Cuando un visitante navega a otros dominios, Visitor. appendvisitoridsto (url) devuelve una URL con ECID adjunta como parámetro de consulta.

   Utilice esta URL para redireccionar desde el dominio original al dominio de destino.

* El código de servicio de ID en el dominio de destino extrae el ECID de la URL en lugar de enviar una solicitud a Adobe para el ID del visitante.

   Esta solicitud incluye el ID de la cookie de terceros, que no está disponible en este caso.

* El código de servicio de ID en la página de destino utiliza el ECID pasado para rastrear al visitante.

   >[!NOTE]
   >Si la página de destino ya tiene un ECID de visitas anteriores, la decisión de sobrescribir la cookie existente está controlada por esta config overwritecrossdomainmcidandaid. Para obtener más información sobre esta configuración, consulte [overwritecrossdomainmcidandaid](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Para obtener más detalles sobre este método, consulte la página [de](/help/library/get-set/appendvisitorid.md) referencia appendvisitoridsto (Seguimiento de dominios cruzados).
