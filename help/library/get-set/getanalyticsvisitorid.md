---
description: Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de ID de visitante se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.
keywords: Servicio de ID de visitante
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 46%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Devuelve el ID de Analytics heredado (si lo hay) que se haya almacenado en la cookie s_vi antes de que el servicio de ID de visitante se implementara. Devuelve una cadena vacía en el caso de que al visitante no se le hubiera asignado nunca un ID de Analytics.

**Sintaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren leer el ID de visitante. No se utiliza en una implementación estándar. `getAnalyticsVisitorID` también funciona con funciones de devolución de llamada para leer identificadores de Analytics e incluirlos en su sistema o aplicación.

**Código de ejemplo**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Si es cliente de Analytics, compruebe y envíe también el ID de Analytics a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del lado del servidor que utiliza la API de inserción de datos. En este caso, debe recopilar y devolver los ID de visitante de ECID y Analytics. Consulte [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**El parámetro “aid” es un valor heredado**

El `aid` parámetro aparece en una cadena de consulta bajo dos conjuntos diferentes de condiciones.

**Caso 1**

Verá el parámetro `aid` en una cadena de consulta cuando:

* El servicio de ID de visitante se implementa correctamente.
* El usuario que visita un sitio tiene un ID de Analytics preexistente almacenado en su [cookie s_vi](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=es#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Verá el parámetro `aid` en una cadena de consulta cuando su organización esté usando un [período de gracia](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) antes de implementar completamente el servicio de ID de visitante. Si el usuario que visita su sitio es nuevo y no está usando un período de gracia, el visitante obtendrá el parámetro `mid` (ECID).

>[!MORELIKETHIS]
>
>* [Cookies de Analytics](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-privacy.html?lang=es)

