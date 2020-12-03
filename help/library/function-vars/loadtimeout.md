---
description: Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar otras soluciones (por ejemplo, Analytics, Audience Manager, Destinatario, etc.) cuánto tiempo debe esperar una respuesta del servicio de ID.
keywords: ID Service
seo-description: Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar otras soluciones (por ejemplo, Analytics, Audience Manager, Destinatario, etc.) cuánto tiempo debe esperar una respuesta del servicio de ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 14%

---


# loadTimeout{#loadtimeout}

Establece un intervalo de tiempo de espera en milisegundos. Se utiliza para indicar otras soluciones (por ejemplo, Analytics, Audience Manager, Destinatario, etc.) cuánto tiempo debe esperar una respuesta del servicio de ID.

**Sintaxis:** ` loadTimeout: *`intervalo en milisegundos`*`

El valor predeterminado es 30.000 milisegundos (30 segundos). Se recomienda enfáticamente que *no cambie* el valor predeterminado.

>[!NOTE]
>
>Las llamadas al servicio de ID son asíncronas con respecto a otros códigos en la página que no sean de Adobe. Como resultado, aumentar o disminuir el intervalo de tiempo de espera no cambia la velocidad a la que la página procesa el contenido. Sin embargo, los intervalos de tiempo de espera largos pueden afectar a los tiempos de carga de la página medidos por las herramientas de supervisión de red comunes, pero el tiempo de procesamiento no se ve afectado.

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

