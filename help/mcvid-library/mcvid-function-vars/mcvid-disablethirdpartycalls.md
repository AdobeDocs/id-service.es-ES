---
description: Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.
keywords: cross domain tracking; Servicio de ID
seo-description: Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e 92 ce 1 f 5-67 a 4-476 c -9 d 04-41 d 4 e 96 b 1592
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.

**Sintaxis:**` `Disablethirdpartycalls: true | false «(el valor predeterminado `false`es.)

Si el método `disableThirdPartyCalls: true`, el servicio de ID no llama a otros dominios.

**Finalidad**

Esta variable se ha pensado para clientes en estos casos:

* Que necesiten impedir que el servicio de ID realice llamadas desde sus páginas seguras y autenticadas.
* Que necesiten que los visitantes del sitio dispongan de un Experience Cloud ID (MID).
* Que necesiten que las otras soluciones de Experience Cloud funcionen correctamente.

**Estrategia de implementación**

Dado que otras soluciones de Experience Cloud se basan en el MID, el servicio de ID llama a Adobe para devolver y establecer este ID. Si necesita hacer que el servicio de ID deje de realizar llamadas desde secciones autenticadas del sitio web, permita que realice las llamadas oportunas desde páginas que no requieran primero autenticación. Una vez que el visitante del sitio dispone de un MID, podrá establecer `disableThirdPartyCalls= true` en el código del servicio de ID dentro de las secciones autenticadas del sitio. En este caso, se entiende que la mayoría de los clientes, si no todos, navegará a una página de autenticación antes de obtener acceso a las partes seguras del sitio.

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

