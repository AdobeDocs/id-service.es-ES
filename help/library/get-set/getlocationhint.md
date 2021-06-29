---
description: Devuelve el ID de región del servicio de Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.
keywords: Servicio de ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '185'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Devuelve el ID de región del servicio de Experience Cloud ID. Un ID de región (o indicio de ubicación) es un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. Necesita el ID de región para realizar llamadas de API del lado del servidor a Audience Manager.

**Sintaxis:** ` var *`nombre de variable`* = visitor.getLocationHint()`

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
