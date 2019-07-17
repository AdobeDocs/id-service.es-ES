---
description: Una visión general del proceso de solicitud y respuesta de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
keywords: Servicio de ID
seo-description: Una visión general del proceso de solicitud y respuesta de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
seo-title: Cómo solicita y establece los ID el servicio de identidad de Experience Cloud
title: Cómo solicita y establece los ID el servicio de identidad de Experience Cloud
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# How the Experience Cloud Identity Service requests and sets IDs{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Una visión general del proceso de solicitud y respuesta de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.

>[!NOTE]
>
>If you're not familiar with how the Experience Cloud Identity Service creates the visitor ID, take a moment to review [Experience Cloud](../introduction/cookies.md).

**Sugerencia:** Vea también nuestro[ vídeo sobre el servicio de ID acerca del seguimiento entre dominios](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html).

## Solicitud de un Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

Los siguientes ejemplos muestran la manera en la que el servicio de ID solicita y recibe el ID de visitante de Experience Cloud. Estos ejemplos usan dos empresas ficticias, la Empresa alimentaria y la Empresa de deporte, para mostrar los flujos de datos para las solicitudes de ID y las respuestas. Cada empresa posee un ID de organización de Experience Cloud único y tiene implementado el código de servicio de ID en todos sus sitios. Estos casos de uso representan flujos de datos para una implementación de servicio de ID genérica sin Analytics, ID heredados o exploradores que bloquean cookies de terceros.

![](assets/sample_sites.png)

**Primera solicitud**

En este ejemplo, un nuevo visitante llega al sitio de pizzas administrado por la Empresa alimentaria. La Empresa alimentaria tiene un código de servicio de ID en el sitio web de pizzas. Cuando se carga el sitio de pizzas, el código de servicio de ID comprueba la cookie AMCV en el dominio de pizzas.

* Si se establece la cookie AMCV, el visitante del sitio tiene un Experience Cloud ID. En este caso, la cookie rastrea al visitante y comparte datos con otras soluciones de Experience Cloud.
* Si la cookie AMCV no se establece, el código de servicio de ID llama a un [servidor de recopilación de datos](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html) (DCS) regional en `dpm.demdex.net/id` (consulte también [Explicación de las llamadas al dominio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)). La llamada incluye el ID de organización de la Empresa Alimentaria. El ID de organización se establece en la función `Visitor.getInstance` del código de servicio de ID.

![](assets/request1.png)

**Primera respuesta**

En la respuesta, el DCS devuelve el ID de [!DNL Experience Cloud] (MID) y la cookie demdex. El código de servicio de ID escribe el valor de MID en la cookie AMCV. Por ejemplo, pongamos que el DCS devuelve un valor MID de 1234. La cookie AMCV se almacenaría como `mid|1234` y se establecería en el dominio de pizzas de origen. La cookie demdex contiene también un ID único (vamos a llamarlo 5678). Esta cookie se establece en el dominio demdex.net de terceros, que es independiente del dominio de pizzas.

![](assets/response1.png)

Como verá en el ejemplo siguiente, el ID de demdex y el ID de organización permiten que el servicio de ID cree y devuelva el MID correcto cuando nuestro visitante se desplace a otro sitio perteneciente a la Empresa alimentaria.

## Solicitud y respuesta entre sitios {#section-15ea880453af467abd2874b8b4ed6ee9}

En este ejemplo, nuestro visitante de la Empresa alimentaria navega al sitio de tacos desde el sitio de pizzas. La Empresa alimentaria tiene un código de servicio de ID en el sitio web de tacos. El visitante nunca había estado en el sitio web de tacos.

En estas condiciones, no hay una cookie AMCV en el sitio de tacos. Además, el servicio de ID no puede utilizar la cookie AMCV establecida en el sitio de pizzas porque es específica para el dominio de pizzas. En consecuencia, el servicio de ID debe llamar al DCS para comprobar y solicitar un ID de visitante. En este caso, la llamada del DCS incluye el ID de organización de la Empresa alimentaria *y* el ID de demdex. Y recuerde, el ID de demdex se recoge del sitio de pizzas y se almacena como una cookie de terceros bajo el dominio demdex.net.

![](assets/request2.png)

Una vez que el DCS recibe el ID de organización y el ID de demdex, crea y devuelve el MID correcto para nuestro visitante del sitio. Dado que el se deriva matemáticamente del ID de organización y del ID de demdex, la cookie AMCV contiene el valor de MID, `mid = 1234`mid = .

![](assets/response2.png)

## Solicitudes de ID de otros sitios {#section-ba9a929e50d64b0aba080630fd83b6f1}

En este ejemplo, nuestro visitante abandona los sitios de la Empresa alimentaria y navega al sitio de fútbol propiedad de la Empresa de deporte. Cuando el visitante llega al sitio de fútbol, el proceso de comprobación y solicitud del ID funciona del mismo modo descrito en los ejemplos anteriores. No obstante, dado que la Empresa de deporte posee su ID de organización propio, el servicio de ID devuelve un MID diferente. El nuevo MID es único para los dominios controlados por la Empresa de deporte y permite que esta empresa siga y comparta los datos del visitante entre soluciones en [!DNL Experience Cloud]. El ID de demdex sigue siendo el mismo para este visitante, ya que está contenido en una cookie de terceros y se mantiene entre dominios distintos.

![](assets/req_resp.png)

