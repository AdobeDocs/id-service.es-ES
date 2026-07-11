---
description: getMarketingCloudVisitorID devuelve el ECID.
keywords: Servicio de ID de visitante
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID devuelve el ECID.

**Sintaxis:** `var *`nombre de variable`* = visitor.getMarketingCloudVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren leer el ID de visitante. No se utiliza en una implementación estándar. `getMarketingCloudVisitorID` también funciona con funciones de devolución de llamada para leer identificadores de Analytics e incluirlos en su sistema o aplicación.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Si es cliente de Analytics, compruebe y envíe también el ID de Analytics a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del lado del servidor que utiliza la API de inserción de datos. En este caso, debe recopilar y devolver los ID de visitante de ECID y Analytics. Consulte [Obtención de ID de visitante de Analytics](../../library/get-set/getanalyticsvisitorid.md).

