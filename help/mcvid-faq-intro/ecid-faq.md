---
description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.
keywords: Servicio de ID
seo-description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.
seo-title: Preguntas más frecuentes sobre el servicio de ID
title: Preguntas más frecuentes sobre el servicio de ID
uuid: e 8 d 8 f 819-3 d 73-4 fa 2-864 c -4867071 c 14 ee
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Preguntas más frecuentes sobre el servicio de ID{#id-service-faqs}

Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.

## Funcionalidad {#section-659e89f8b9a74cb8afff35587dc96836}

**¿Qué tipo de funcionalidad o capacidades proporciona el servicio de ID?**

Consulte la [Información general](../mcvid-introduction/mcvid-overview.md).

**¿Por qué el servicio de ID no está realizando una llamada para recuperar el Experience Cloud ID?**

Esto puede ser difícil de diagnosticar. Una cosa que puede comprobar son los encabezados de política de seguridad de contenido de su sitio. Si tiene una política de seguridad estricta, esa configuración puede bloquear las llamadas de terceros realizadas por el servicio de ID. Consulte [Políticas de seguridad del contenido y el servicio Experience Cloud ID](../mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Almacenamiento del archivo VisitorAPI.js**

Puede experimentar problemas si aloja VisitorAPI.js como archivo local en aplicaciones móviles. Se recomienda alojar el archivo en un servidor web.

## Latencia y tiempos de carga de página {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**¿Cómo afecta la ubicación de la biblioteca VisitorAPI.js del servicio de ID a los tiempos de carga de las páginas?**

Coloque la biblioteca visitorapi. js en la parte superior de la página en la `<head>` sección de su código. Esto le ayuda a garantizar que la llamada de un ID se emita antes de que el cuerpo de la página empiece a cargarse y que aumenten las posibilidades de que se devuelva un ID correctamente.

La llamada de servicio de ID es asíncrona y es la única llamada al [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html). La llamada al servicio de ID no impide que otros elementos se carguen en la página.

Para [!DNL Target] los clientes, la colocación de código de servicio de ID en la `<body>` página puede aumentar las probabilidades de que pudiera bloquear una [!DNL Target] llamada. Si debe colocar el código de servicio de ID en el cuerpo de la página, debe colocarse después de la `<body>` etiqueta abierta.

**¿Con cada carga de página, realiza el servicio de ID una llamada al servidor?**

No, esta llamada solo se producirá la primera vez que se procese la página y, posteriormente, una vez cada 7 días. Mientras tanto, no se necesitarán las llamadas al servidor. El servicio de ID funciona en el modo del lado del cliente y no necesita realizar una llamada al servidor para devolver un ID.

Consulte [Información general](../mcvid-introduction/mcvid-overview.md).

**Al utilizar el servicio de ID, ¿qué puede ralentizar los tiempos de carga de las páginas o repercutir en la experiencia del usuario?**

Es difícil catalogar todas las condiciones posibles. Miles de millones de clientes consumidores se conectan a nuestros servicios, y la gran variedad de lugares y maneras que utilizan para conectarse repercuten en el rendimiento. Por ejemplo:

* Las velocidades varían enormemente en las redes móviles. Estas redes también se ven afectadas por la pérdida de señales y datos o paquetes de voz.
* La conectividad también se ve afectada en los dispositivos que se conectan a través de WiFi en diferentes condiciones. Por ejemplo, la pérdida de paquetes y los problemas de velocidad son habituales en los lugares públicos, como las cafeterías o en otros entornos, como un avión, en el que los paquetes deben rebotar a través de un satélite antes de alcanzar las redes terrestres.
* Las redes locales mal configuradas pueden influir negativamente en la conectividad y la velocidad.
* Los dispositivos del cliente pueden tener sus propios problemas, como, por ejemplo, la poca memoria, los excesivos cambios de disco o la potencia limitada de la CPU con relación a las cargas de trabajo actuales.
* Los navegadores ponen en cola y ejecutan las llamadas de los servidores remotos e incluso procesan las respuestas con reglas distintas, en función del fabricante y la versión del navegador. Este comportamiento influir en la velocidad y el rendimiento.

**¿Puede indicar algunas mejoras que haya realizado para acortar los tiempos de carga de las páginas?**

Por ejemplo, la separación de procesos. En el caso de que se produzcan varias solicitudes de sincronización de ID, hemos introducido la separación de procesos. En los informes de laboratorio hemos observado que a los clientes que realizan varias sincronizaciones de ID se les bloquea la IU debido a que se produce una gran cantidad de computaciones continuas de CPU. En consecuencia, hemos introducido la separación de procesos para dividir las solicitudes de sincronización de ID en cada 100 ms cada una.

Este cambio mejora el rendimiento de los clientes que utilizan Visitor 2.3.0 o posterior y DIL 6.10 o posterior. Las mejoras de los tiempos de carga de las páginas se muestran en la imagen siguiente:

![](assets/id_sync_improvements_copy.png)

**¿Las solicitudes de los navegadores que utilizan CORS en lugar de JSONP afectan al rendimiento de la página?**

Las solicitudes de recursos con CORS generalmente son más preferibles que con JSONP. Gracias a JSONP, algunos navegadores ponen en cola y derogan la prioridad de las solicitudes relativas a otras llamadas síncronas y asíncronas en la página. CORS ayuda a garantizar que estas solicitudes sean tratadas con una prioridad mayor en la pila de llamadas del navegador.

Consulte [Compatibilidad con CORS en el servicio Experience Cloud ID](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Seguridad {#section-b176b8492fbe4acfb79ebb30ec902f98}

**¿El servicio de ID es compatible con CORS?**

Sí. Consulte [Compatibilidad con CORS en el servicio Experience Cloud ID](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**¿Qué es CORS?**

*`Cross-Origin Resource Sharing`* o CORS, es un método que los navegadores utilizan para solicitar recursos. El servicio de ID siempre solicita recursos mediante CORS en los navegadores que lo admiten. El servicio de ID solicita recursos con JSONP en navegadores más antiguos que no admiten CORS. Consulte [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**¿Qué sucede si mis requisitos de seguridad son tan estrictos que nunca deseo usar JSONP?**

Si tiene requisitos de seguridad estrictos, establezca la configuración de la API del servicio de ID `useCORSOnly: true`. Solo debe habilitar este modo si está seguro de que los visitantes del sitio utilizan navegadores compatibles con CORS.

Consulte [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758) y [usecorsonly](../mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORE_ LIKE_ THIS]
>
>* [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html)

