---
description: Establece un intervalo de tiempo de espera en milisegundos. Se usa para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo se debe esperar una respuesta del servicio de ID.
keywords: Servicio de ID
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '140'
ht-degree: 100%

---

# loadTimeout{#loadtimeout}

Establece un intervalo de tiempo de espera en milisegundos. Se usa para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo se debe esperar una respuesta del servicio de ID.

**Sintaxis:** ` loadTimeout: *`intervalo en milisegundos`*`

El valor predeterminado es de 30 000 milisegundos (30 segundos). Se recomienda encarecidamente *no* cambiar el valor predeterminado.

>[!NOTE]
>
>Las llamadas al servicio de ID son asíncronas con respecto a otros códigos en la página que no sean de Adobe. Como resultado, aumentar o reducir el intervalo de tiempo de espera no cambia la velocidad a la que la página procesa el contenido. Sin embargo, los intervalos de tiempo de espera largos pueden afectar a los tiempos de carga de las páginas que miden las herramientas de monitorización de red comunes, pero el tiempo de procesamiento no se ve afectado.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
