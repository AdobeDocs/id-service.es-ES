---
description: Esta configuración le permite limpiar ECID huérfanos o inactivos (ECID) en función de la versión del servicio de ID de visitante que se está actualizando.
keywords: Servicio de ID de visitante
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 41%

---

# resetBeforeVersion{#resetbeforeversion}

Esta configuración le permite limpiar ECID huérfanos o inactivos (ECID) en función de la versión del servicio de ID de visitante que se está actualizando.

Si se proporciona la versión del servicio de ID de visitante como valor de la variable `resetBeforeVersion`, los ECID obsoletos se borrarán de los ID del lado del cliente.

Algunas condiciones, como los tiempos de espera de sesión, a veces podían provocar que se generara un ID del lado del cliente sin que el servicio de ID de visitante obtuviera correctamente un ID del lado del servidor. Cuando esto sucede, el servicio de ID de visitante rastrea el ID del lado del cliente huérfano sin la capacidad de realizar un seguimiento entre dominios o de sincronizarse correctamente con otras soluciones. El comportamiento compara la versión de la cookie AMCV actual con el valor de `resetBeforeVersion`. Si la cookie no existe o su versión es menor (más antigua) que la versión más reciente de `resetBeforeVersion`, la cookie AMCV se eliminará y el servicio de identificación del visitante solicitará un nuevo ECID.

Para los visitantes que tienen cookies demdex de terceros en el navegador, se comprueba el ECID para ver si se generó correctamente empleando el UUID de la cookie. Si esa comprobación resulta verdadera, el nuevo ECID será el mismo y el visitante se considerará nuevo. Si, por alguna razón, el ECID que se está borrando no se generó mediante la cookie Demdex, o si no hay ninguna cookie Demdex, el visitante recibirá un nuevo ECID y se considerará como nuevo.

**Sintaxis:** `resetBeforeVersion = "3.3"`

**Ejemplo de código**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
  
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

