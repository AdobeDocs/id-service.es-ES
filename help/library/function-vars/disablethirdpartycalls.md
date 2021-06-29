---
description: Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.
keywords: seguimiento entre dominios;servicio de ID
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicador booleano opcional que impide que el servicio de ID realice llamadas a otros dominios.

**Sintaxis:** ` ` disableThirdPartyCalls: true false`` (el valor predeterminado es `false`).

Si el método `disableThirdPartyCalls: true`, el servicio de ID no llama a otros dominios.

**Finalidad**

Esta variable está diseñada para los clientes:

* Que necesiten evitar que el servicio de ID realice llamadas desde sus páginas seguras y autenticadas.
* Que necesiten que los visitantes del sitio dispongan de un Experience Cloud ID (MID).
* Cuyas otras soluciones de Experience Cloud deban funcionar correctamente.

**Estrategia de implementación**

Dado que otras soluciones de Experience Cloud dependen del MID, el servicio de ID llama a Adobe para devolver y establecer este ID. Si necesita hacer que el servicio de ID deje de realizar llamadas desde secciones autenticadas del sitio web, permita que realice las llamadas oportunas desde páginas que no requieran primero autenticación. Una vez que el visitante del sitio dispone de un MID, podrá establecer `disableThirdPartyCalls= true` en el código del servicio de ID dentro de las secciones autenticadas del sitio. Aquí se supone que la mayoría, si no todos, de los clientes navegarán a una página de autenticación antes de obtener acceso a las partes seguras del sitio.

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
