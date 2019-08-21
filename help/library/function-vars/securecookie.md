---
description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

