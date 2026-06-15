---
description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
keywords: Servicio de ID
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 100%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.

**Sintaxis:** `var *`nombre de variable`* = visitor.getMarketingCloudVisitorID()`

Normalmente, esta función se utiliza con soluciones personalizadas que requieren leer el ID de visitante. No se utiliza en una implementación estándar. `getMarketingCloudVisitorID` funciona también con funciones de llamada de retorno para leer [!DNL Analytics] ID de e incluirlos en su sistema o aplicación.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Si usted es [!DNL Analytics] cliente de, compruebe y envíe también el [!DNL Analytics] ID de a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del lado del servidor que utiliza la API de inserción de datos. En este caso, deberá recopilar y devolver los ID de visitante de [!DNL Experience Cloud] y [!DNL Analytics]. Consulte [Obtención de ID de visitante de Analytics](../../library/get-set/getanalyticsvisitorid.md).

