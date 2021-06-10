---
description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.
keywords: 'Servicio de ID '
title: Preguntas más frecuentes sobre el servicio de ID
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Preguntas más frecuentes sobre el servicio de ID {#id-service-faqs}

Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos al uso del servicio de ID.

## Funcionalidad {#section-659e89f8b9a74cb8afff35587dc96836}

**¿Qué tipo de funcionalidad o capacidades proporciona el servicio de ID?**

Consulte la [Información general](../introduction/overview.md).

**¿Por qué el servicio de ID no está realizando una llamada para recuperar el Experience Cloud ID?**

Esto puede ser difícil de diagnosticar. Una cosa que puede comprobar son los encabezados de las directivas de seguridad de contenido del sitio. Si tiene una política de seguridad estricta, esa configuración puede bloquear las llamadas de terceros realizadas por el servicio de ID. Consulte [Políticas de seguridad de contenido y el servicio de Experience Cloud ID](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Almacenamiento del archivo VisitorAPI.js**

Es posible que tenga problemas si aloja VisitorAPI.js como archivo local en aplicaciones móviles. Le recomendamos que aloje el archivo en un servidor web.

## Tiempos de carga de las páginas y latencia {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**¿Cómo afecta la ubicación de la biblioteca VisitorAPI.js del servicio de ID a los tiempos de carga de las páginas?**

Coloque la biblioteca VisitorAPI.js en la parte superior de la página en la `<head>` sección de su código. Esto le ayuda a garantizar que la llamada de un ID se emita antes de que el cuerpo de la página empiece a cargarse y que aumenten las posibilidades de que se devuelva un ID correctamente.

La llamada del servicio de ID es asincrónica y es la única llamada al [dominio demdex.net](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/reference/demdex-calls.html). La llamada al servicio de ID no impide que otros elementos se carguen en la página.

En el caso de los [!DNL Target] clientes de, al colocar el código de servicio de ID en la etiqueta `<body>` de la página, pueden incrementar las probabilidades de que se bloquee una llamada de [!DNL Target]. Si debe colocar el código de servicio de ID en el cuerpo de la página, se debe colocar después de la etiqueta `<body>` de apertura.

**¿Hace el servicio de ID una llamada al servidor con cada carga de página?**

No, esta llamada solo se realizará la primera vez que la página se procese y una vez cada 7 días a partir de entonces. Mientras tanto, no se requieren llamadas al servidor. El servicio de ID funciona del lado del cliente y no necesita realizar una llamada al servidor para devolver un ID.

Consulte [Información general](../introduction/overview.md).

**Al utilizar el servicio de ID, ¿qué puede causar tiempos de carga de página lentos o afectar a la experiencia del usuario?**

Es difícil catalogar todas las condiciones posibles. Miles de millones de clientes se conectan a nuestros servicios y la gran variedad de ubicaciones y métodos de conexión afectan al rendimiento. Por ejemplo:

* Las velocidades varían considerablemente en las redes móviles. Estas redes también sufren la pérdida de señales y datos o de paquetes de voz.
* La conectividad sufre en los dispositivos que se conectan a través de WiFi en diversas condiciones. Por ejemplo, la pérdida de paquetes y los problemas de velocidad son comunes en lugares públicos como cafeterías o en otros entornos como aviones, donde los paquetes deben rebotar a través de un satélite antes de llegar a las redes terrestres.
* Las redes locales mal configuradas pueden afectar negativamente a la conectividad y la velocidad.
* Los dispositivos cliente pueden tener sus propios problemas, como memoria baja, exceso de intercambio de discos o potencia de CPU limitada en relación con las cargas de trabajo actuales.
* Los navegadores ponen en cola y ejecutan llamadas al servidor remoto e incluso procesan las respuestas con reglas diferentes, según el fabricante y la versión del explorador. Este comportamiento afecta a la velocidad y al rendimiento.

**¿Puede nombrar algunas mejoras que ha realizado para reducir los tiempos de carga de las páginas?**

Por ejemplo, la producción de subprocesos. Hemos introducido el rendimiento de subprocesos en caso de varias solicitudes de sincronización de ID. En los informes de laboratorio observamos que, para los clientes que realizan varias sincronizaciones de ID, la interfaz de usuario se bloquea debido a que se producen muchos cálculos de CPU continuos. Como resultado, hemos introducido el rendimiento de subprocesos para separar las solicitudes de sincronización de ID en 100 ms cada una.

Este cambio mejora el rendimiento de los clientes que utilizan Visitor 2.3.0 o posterior y DIL 6.10 o posterior. Las mejoras en los tiempos de carga de la página se muestran en la siguiente imagen:

![](assets/id_sync_improvements_copy.png)

**¿Afectan las solicitudes de explorador que utilizan CORS y JSON-P al rendimiento de la página?**

Las solicitudes de recursos con CORS son generalmente más preferibles que con JSONP. Con JSONP, algunos exploradores ponen en cola y restan prioridad a las solicitudes en relación con otras llamadas sincrónicas y asincrónicas de la página. CORS ayuda a garantizar que estas solicitudes se traten con mayor prioridad en las llamadas del explorador.

Consulte [Compatibilidad con COPPA en el servicio de Experience Cloud ID](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Seguridad {#section-b176b8492fbe4acfb79ebb30ec902f98}

**¿Admite CORS el servicio de ID?**

Sí. Consulte [Compatibilidad con COPPA en el servicio de Experience Cloud ID](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**¿Qué es CORS?**

*`Cross-Origin Resource Sharing`* o CORS, es un método que los navegadores utilizan para solicitar recursos. El servicio de ID siempre solicita recursos mediante CORS en navegadores que lo admiten. El servicio de ID solicita recursos con JSON-P en exploradores más antiguos que no admiten CORS. Consulte [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**¿Qué sucede si mis requisitos de seguridad son tan estrictos que nunca deseo usar JSONP?**

Si tiene requisitos de seguridad estrictos, establezca la configuración de la API del servicio de ID `useCORSOnly: true`. Solo debe habilitar este modo si está seguro de que los visitantes del sitio utilizan navegadores compatibles con CORS.

Consulte [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) y [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html)

