---
description: Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo deben esperar para obtener una respuesta del servicio de ID.
keywords: Servicio de ID
seo-description: Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo deben esperar para obtener una respuesta del servicio de ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f 627 e 044-bd 73-49 a 4-8 a 90-6 d 19 aa 566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar a otras soluciones (por ejemplo, Analytics, Audience Manager, Target, etc.) cuánto tiempo deben esperar para obtener una respuesta del servicio de ID.

**Sintaxis:**` loadTimeout: *`intervalo en milisegundos`*`

El valor predeterminado es 30 000 milisegundos (30 segundos). Le recomendamos encarecidamente que *no* cambie el valor predeterminado.

>[!NOTE]
>
>Las llamadas al servicio de ID son asíncronas en relación con otros códigos que no sean de Adobe en la página. En consecuencia, si se aumenta o se reduce el intervalo de tiempo límite, no se modifica la velocidad a la que su página procesa el contenido. No obstante, los intervalos de tiempo límite largos pueden afectar a los tiempos de carga de la página medidos con las herramientas de control de una red común, pero el tiempo de procesamiento no se ve afectado.

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

