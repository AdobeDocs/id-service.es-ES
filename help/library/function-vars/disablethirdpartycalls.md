---
description: Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.
keywords: cross domain tracking;ID Service
seo-description: Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 63%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.

**Sintaxis:** ` ` disableThirdPartyCalls: true|false`` (el valor predeterminado es `false`).

Si el método `disableThirdPartyCalls: true`, el servicio de ID no llama a otros dominios.

**Finalidad**

Esta variable está diseñada para clientes que necesitan:

* Para evitar que el servicio de ID realice llamadas desde sus páginas seguras y autenticadas.
* Que necesiten que los visitantes del sitio dispongan de un Experience Cloud ID (MID).
* Sus otras soluciones Experience Cloud para funcionar correctamente.

**Estrategia de implementación**

Dado que otras soluciones Experience Cloud dependen del MID, el servicio de ID llama al Adobe para devolver y establecer este ID. Si necesita hacer que el servicio de ID deje de realizar llamadas desde secciones autenticadas del sitio web, permita que realice las llamadas oportunas desde páginas que no requieran primero autenticación. Una vez que el visitante del sitio dispone de un MID, podrá establecer `disableThirdPartyCalls= true` en el código del servicio de ID dentro de las secciones autenticadas del sitio. La suposición aquí es que la mayoría de los clientes, si no todos, navegarán a una página de autenticación antes de obtener acceso a las partes seguras del sitio.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

