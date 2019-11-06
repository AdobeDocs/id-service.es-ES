---
description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
keywords: Servicio de ID
seo-description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.

**Sintaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren la lectura del ID de visitante. No se utiliza en las implementaciones estándares. `getAnalyticsVisitorID` funciona también con funciones de llamada de retorno para leer [!DNL Analytics] ID de e incluirlos en su sistema o aplicación.

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
>Si usted es [!DNL Analytics] cliente de, compruebe y envíe también el [!DNL Analytics] ID de a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del lado del servidor que utiliza la API de inserción de datos. En este caso, deberá recopilar y devolver los ID de visitante de [!DNL Experience Cloud] y [!DNL Analytics]. Consulte [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**El parámetro “aid” es un valor heredado**

El `aid` parámetro aparece en una cadena de consulta bajo dos conjuntos diferentes de condiciones.

**Caso 1**

Verá el parámetro `aid` en una cadena de consulta cuando:

* El servicio de ID de [!DNL Experience Cloud] se implementa correctamente.
* El usuario que visite un sitio tiene un ID de [!DNL Analytics] preexistente almacenado en su [cookie s_vi](https://marketing.adobe.com/resources/help/es_ES/whitepapers/cookies/cookies_analytics.html).

**Caso 2**

Verá el `aid` parámetro en una cadena de consulta cuando su organización utilice un [periodo de gracia](../../reference/analytics-reference/grace-period.md) antes de implementar completamente el servicio de ID. Si el usuario que visita su sitio es nuevo y no está usando un período de gracia, el visitante obtendrá el parámetro `mid` (ID de [!DNL Experience Cloud]).

>[!MORELIKETHIS]
>
>* [Cookies de Analytics](https://marketing.adobe.com/resources/help/es_ES/whitepapers/cookies/cookies_analytics.html)

