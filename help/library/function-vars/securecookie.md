---
description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

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
