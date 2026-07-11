---
description: Devuelve el ID de región del servicio de ID de visitante. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID de visitante en particular. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
keywords: Servicio de ID de visitante
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 196
ht-degree: 70%

---

# getLocationHint{#getlocationhint}

Devuelve el ID de región del servicio de ID de visitante. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID de visitante en particular. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.

**Sintaxis:** `var *`nombre de variable`* = visitor.getLocationHint()`

Para obtener una lista de ID de región y sus ubicaciones correspondientes, consulte [ID de región de DCS, ubicaciones y nombres de host](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=es).

**Ejemplo de código**

La función de indicio de ubicación lee el ID de región de la cookie AMCV. Si el ID de región ya está establecido en la cookie AMCV, la llamada de retorno se produce inmediatamente. Si el ID de región no está establecido, la función esperará una respuesta del servidor antes de pasar el ID de región a la rellamada. Su código podría ser similar al del siguiente ejemplo.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

