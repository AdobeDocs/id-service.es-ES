---
description: Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo se debe esperar una respuesta del servicio de ID de visitante.
keywords: Servicio de ID de visitante
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 56%

---

# loadTimeout{#loadtimeout}

Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo se debe esperar una respuesta del servicio de ID de visitante.

**Sintaxis:** `loadTimeout: *`intervalo en milisegundos`*`

El valor predeterminado es de 30 000 milisegundos (30 segundos). Se recomienda encarecidamente *no* cambiar el valor predeterminado.

>[!NOTE]
>
>Las llamadas al servicio de ID de visitante son asíncronas con respecto a otros códigos de la página que no sean de Adobe. Como resultado, aumentar o reducir el intervalo de tiempo de espera no cambia la velocidad a la que la página procesa el contenido. Sin embargo, los intervalos de tiempo de espera largos pueden afectar a los tiempos de carga de las páginas que miden las herramientas de monitorización de red comunes, pero el tiempo de procesamiento no se ve afectado.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

