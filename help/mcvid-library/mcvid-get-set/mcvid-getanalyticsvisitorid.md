---
description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
keywords: Servicio de ID
seo-description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.

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
>Si [!DNL Analytics] es cliente, compruebe y envíe [!DNL Analytics] el ID a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del servidor que utiliza la API de inserción de datos. En este caso, debe recopilar y devolver las ID [!DNL Experience Cloud] y los [!DNL Analytics] ID de visitante. Consulte [getmarketingcloudvisitorid](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md).

**El parámetro “aid” es un valor heredado**

El parámetro `aid` aparece en una cadena de consulta bajo dos conjuntos diferentes de condiciones.

**Caso 1**

Verá el parámetro `aid` en una cadena de consulta cuando:

* El servicio [!DNL Experience Cloud] de ID se implementa correctamente.
* El usuario que visite un sitio tiene un ID de [!DNL Analytics] preexistente almacenado en su [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

Verá el `aid` parámetro en una cadena de consulta cuando su organización utilice un período [de gracia](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) antes de implementar completamente el servicio de ID. Si el usuario que visita el sitio es nuevo y no utiliza un período de gracia, el visitante obtendrá el `mid` parámetro [!DNL Experience Cloud] (ID).

>[!MORE_ LIKE_ THIS]
>
>* [Cookies de Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

