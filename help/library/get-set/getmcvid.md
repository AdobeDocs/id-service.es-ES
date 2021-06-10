---
description: getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.
keywords: Servicio de ID
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID devuelve el ID de visitante de Experience Cloud.

**Sintaxis:** ` var *`nombre de variable`* = visitor.getMarketingCloudVisitorID()`

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
