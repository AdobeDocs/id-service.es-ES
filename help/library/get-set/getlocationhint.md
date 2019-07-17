---
description: Devuelve el ID de región del servicio de identidad de Experience Cloud. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
keywords: Servicio de ID
seo-description: Devuelve el ID de región del servicio de identidad de Experience Cloud. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

Devuelve el ID de región del servicio de identidad de Experience Cloud. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.

**Sintaxis:** ` var *`nombre de variable`* = visitor.getLocationHint()`

Para obtener una lista de ID de región y las ubicaciones correspondientes, consulte [DCS Region IDs, Locations, and Host Names](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html) (ID de región de DCS, ubicaciones y nombres de host).

**Ejemplo de código**

La función de indicio de ubicación lee el ID de región desde la cookie de AMCV. Si el ID de región ya se ha establecido en la cookie de AMCV, entonces la rellamada se produce de manera inmediata. Si no se ha establecido el ID de región, la función esperará a obtener una respuesta del servidor antes de pasar el ID de región a la rellamada. Su código podría ser similar al del siguiente ejemplo.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

