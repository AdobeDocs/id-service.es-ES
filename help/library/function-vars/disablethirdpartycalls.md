---
description: Un indicador booleano opcional que evita que el servicio de ID de visitante realice llamadas a otros dominios.
keywords: seguimiento entre dominios;Servicio de ID de visitante
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicador booleano opcional que evita que el servicio de ID de visitante realice llamadas a otros dominios.

**Sintaxis:** ` ` disableThirdPartyCalls: true false`` (el valor predeterminado es `false`).

Cuando `disableThirdPartyCalls: true`, el servicio de ID de visitante no realizará llamadas a otros dominios.

**Finalidad**

Esta variable está diseñada para los clientes:

* Para evitar que el servicio de ID de visitante realice llamadas desde sus páginas seguras y autenticadas.
* Que los visitantes del sitio tengan un ECID.
* Sus otras soluciones CX Enterprise funcionan correctamente.

**Estrategia de implementación**

Dado que otras soluciones de CX Enterprise dependen del MID, el servicio de ID de visitante llama a Adobe para devolver y establecer este ID. Si necesita hacer que el servicio de ID de visitante deje de realizar llamadas desde secciones autenticadas del sitio web, permita que realice las llamadas oportunas desde páginas que no requieran primero autenticación. Una vez que el visitante del sitio dispone de un MID, podrá establecer `disableThirdPartyCalls= true` en el código del servicio de ID de visitante en las secciones autenticadas del sitio. Aquí se supone que la mayoría, si no todos, de los clientes navegarán a una página de autenticación antes de obtener acceso a las partes seguras del sitio.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

