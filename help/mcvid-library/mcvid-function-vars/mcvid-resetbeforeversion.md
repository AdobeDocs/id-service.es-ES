---
description: Esta configuración le permite limpiar Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.
keywords: Servicio de ID
seo-description: Esta configuración le permite limpiar Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetBeforeVersion{#resetbeforeversion}

Esta configuración le permite limpiar Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.

Si se proporciona la versión del servicio de ID como valor de la variable `resetBeforeVersion`, los ECID obsoletos se borran de los ID del lado del cliente.

Determinadas condiciones, por ejemplo que se supere el tiempo de espera de una sesión, pueden provocar que se genere un ID en el lado del cliente sin que el servicio de ID logre obtener un ID del lado del servidor. Cuando esto sucede, el servicio de ID rastrea un ID huérfano del lado del cliente, pero no le es posible ni realizar el seguimiento entre dominios ni sincronizarse adecuadamente con otras soluciones. El comportamiento compara la versión de la cookie AMCV actual con el valor de `resetBeforeVersion`. Si la cookie no existe o su versión es menor (más antigua) que la versión más reciente de `resetBeforeVersion`, la cookie AMCV se elimina y el servicio de ID solicita un nuevo ECID.

Para los visitantes que tienen cookies demdex de terceros en el navegador, se comprueba el ECID para ver si se generó correctamente empleando el UUID de la cookie. Si esta comprobación resulta cierta, el nuevo ECID será el mismo y el visitante será tratado como nuevo. Si, por alguna razón, el ECID analizado no se generó empleando la cookie demdex, o si no existe dicha cookie, el visitante recibirá un nuevo ECID y será tratado como nuevo.

**Sintaxis:** `resetBeforeVersion = "3.3"`

**Ejemplo de código**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

