---
description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
keywords: Servicio de ID
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de Experience Cloud ID se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.

**Sintaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren leer el ID de visitante. No se utiliza en una implementación estándar. `getAnalyticsVisitorID` funciona también con funciones de llamada de retorno para leer [!DNL Analytics] ID de e incluirlos en su sistema o aplicación.

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
* El usuario que visite un sitio tiene un ID de [!DNL Analytics] preexistente almacenado en su [cookie s_vi](https://docs.adobe.com/content/help/es-ES/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Verá el `aid` parámetro en una cadena de consulta cuando su organización utilice un [periodo de gracia](../../reference/analytics-reference/grace-period.md) antes de implementar completamente el servicio de ID. Si el usuario que visita su sitio es nuevo y no está usando un período de gracia, el visitante obtendrá el parámetro `mid` (ID de [!DNL Experience Cloud]).

>[!MORELIKETHIS]
>
>* [Cookies de Analytics](https://docs.adobe.com/content/help/es-ES/core-services/interface/ec-cookies/cookies-privacy.html)

