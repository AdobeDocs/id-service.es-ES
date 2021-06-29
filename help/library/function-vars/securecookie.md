---
description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
keywords: Servicio de ID
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '91'
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
