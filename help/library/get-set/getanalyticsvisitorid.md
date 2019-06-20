---
description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_ vi antes de que se implementara el servicio Experience Cloud ID. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
keywords: Servicio de ID
seo-description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_ vi antes de que se implementara el servicio Experience Cloud ID. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_ vi antes de que se implementara el servicio Experience Cloud ID. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.

**Sintaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren la lectura del ID de visitante. No se utiliza en las implementaciones estándares. `getAnalyticsVisitorID` funciona también con funciones de llamada de retorno para leer ID de [!DNL Analytics] e incluirlos en su sistema o aplicación.

**Código de ejemplo**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del servidor que utiliza la API de inserción de datos. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**El parámetro “aid” es un valor heredado**

El parámetro `aid` aparece en una cadena de consulta bajo dos conjuntos diferentes de condiciones.

**Caso 1**

Verá el parámetro `aid` en una cadena de consulta cuando:

* The [!DNL Experience Cloud] ID service is deployed correctly.
* El usuario que visite un sitio tiene un ID de [!DNL Analytics] preexistente almacenado en su [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ THIS]
>
>* [Cookies de Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

