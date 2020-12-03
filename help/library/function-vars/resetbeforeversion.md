---
description: Esta configuración le permite retirar los Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.
keywords: ID Service
seo-description: Esta configuración le permite retirar los Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 60%

---


# resetBeforeVersion{#resetbeforeversion}

Esta configuración le permite retirar los Experience Cloud ID (ECID) huérfanos o inactivos, en función de la versión del servicio de ID que se está actualizando.

Si se proporciona la versión del servicio de ID como valor de la variable `resetBeforeVersion`, los ECID obsoletos se borran de los ID del lado del cliente.

Algunas condiciones, como los tiempos de espera de sesión, pueden ocasionar que se genere un ID del lado del cliente sin que el servicio de ID obtenga correctamente un ID del lado del servidor. Cuando esto sucede, el servicio de ID rastrea un ID del lado del cliente huérfano sin la capacidad de realizar un seguimiento entre dominios o de sincronizarse correctamente con otras soluciones. El comportamiento compara la versión de la cookie AMCV actual con el valor de `resetBeforeVersion`. Si la cookie no existe o su versión es menor (más antigua) que la versión más reciente de `resetBeforeVersion`, la cookie AMCV se elimina y el servicio de ID solicita un nuevo ECID.

Para los visitantes que tienen cookies demdex de terceros en el navegador, se comprueba el ECID para ver si se generó correctamente empleando el UUID de la cookie. Si esa comprobación resulta verdadera, el nuevo ECID será el mismo y el visitante se considerará nuevo. Si por alguna razón el ECID que se está eliminando no se generó usando la cookie Demdex, o si no hay ninguna cookie Demdex, el visitante recibirá un nuevo ECID y se considerará nuevo.

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

