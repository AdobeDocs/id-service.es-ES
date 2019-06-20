---
description: Devuelve el ID de región del servicio Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
keywords: Servicio de ID
seo-description: Devuelve el ID de región del servicio Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc 312 b 7-d 270-4 a 5 c-a 2 bb -0 fbb 37 f 1 e 2 f 4
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getLocationHint{#getlocationhint}

Devuelve el ID de región del servicio Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico asociado a la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.

**Sintaxis:**` var *`nombre de variable`* = visitor.getLocationHint()`

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

