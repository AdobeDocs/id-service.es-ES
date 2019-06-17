---
description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
keywords: Servicio de ID
seo-description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93 e 16220-b 5 b 3-4 d 81-9189-30031 bc 15129
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.

**Sintaxis:**` var *`nombre de variable`* = visitor.getMarketingCloudVisitorID()`

Este método se emplea generalmente con soluciones personalizadas que necesitan leer el ID de visitante. No se utiliza en las implementaciones estándares. `getMarketingCloudVisitorID` funciona también con funciones de llamada de retorno para leer ID de [!DNL Analytics] e incluirlos en su sistema o aplicación.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>Si [!DNL Analytics] es cliente, compruebe y envíe [!DNL Analytics] el ID a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del servidor que utiliza la API de inserción de datos. En este caso, debe recopilar y devolver las ID [!DNL Experience Cloud] y los [!DNL Analytics] ID de visitante. Consulte [Obtención de ID de visitante de Analytics](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md).

