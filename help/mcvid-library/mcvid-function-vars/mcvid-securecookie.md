---
description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995 d 19 f 6-9 c 9 d -4493-9 c 9 c -545 b 0 b 5696 b 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

Un indicador booleano opcional que añade un atributo “Secure” a la cookie AMCV.

Este atributo de configuración está disponible en `visitorAPI`, versión 3.3.0.

>[!NOTE]
>
>La `SecureCookie` configuración no funcionará en dominios no seguros y podría no recibir los valores MID de las visitas que usan un protocolo no seguro. La configuración `secureCookie` solo debe establecerse en `true` cuando esté seguro de que todas las páginas y subdominios emplean un protocolo seguro en todo momento.

**Sintaxis:**`secureCookie: true | false` (predeterminado)

**Ejemplo de código**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

