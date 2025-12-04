---
description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
keywords: Servicio de ID
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 100%

---

# secureCookie{#securecookie}

Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.

Este atributo de configuración está disponible en `visitorAPI`, versión 3.3.0.

>[!NOTE]
>
>La `SecureCookie` configuración no funciona en dominios no protegidos, lo que podría impedir que reciba los valores MID por las visitas que utilicen un protocolo no protegido. La `secureCookie` configuración solo debe establecerse en `true` cuando esté seguro de que todas las páginas y subdominios emplean un protocolo seguro en todo momento.

**Sintaxis:** `secureCookie: true | false` (predeterminado)

**Ejemplo de código**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

