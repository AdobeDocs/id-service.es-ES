---
description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
keywords: Servicio de ID
seo-description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.

**Sintaxis:** ` var *`nombre de variable`* = visitor.getMarketingCloudVisitorID()`

Este método se emplea generalmente con soluciones personalizadas que necesitan leer el ID de visitante. No se utiliza en las implementaciones estándares. `getMarketingCloudVisitorID` funciona también con funciones de llamada de retorno para leer [!DNL Analytics] ID de e incluirlos en su sistema o aplicación.

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
>Si usted es [!DNL Analytics] cliente de, compruebe y envíe también el [!DNL Analytics] ID de a su función. Por ejemplo, es recomendable contar con ambos identificadores a la hora de pasar el ID de visitante en un elemento de forma oculta a una aplicación del lado del servidor que utiliza la API de inserción de datos. En este caso, deberá recopilar y devolver los ID de visitante de [!DNL Experience Cloud] y [!DNL Analytics]. Consulte [Obtención de ID de visitante de Analytics](../../library/get-set/getanalyticsvisitorid.md).

