---
description: Devuelve el ID de región del servicio de Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
keywords: Servicio de ID
seo-description: Devuelve el ID de región del servicio de Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---

# getLocationHint {#getlocationhint}

Devuelve el ID de región del servicio de Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.

**Sintaxis:** ` var *`nombre de variable`* = visitor.getLocationHint()`

Para obtener una lista de ID de región y sus ubicaciones correspondientes, consulte [ID de región de DCS, ubicaciones y nombres de host](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

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
