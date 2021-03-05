---
description: Una configuración de ECID que puede usarse para permitir cookies AMCV en páginas de AMP de Google.
keywords: Servicio de ID
seo-description: Una configuración de ECID que puede usarse para permitir cookies AMCV en páginas de AMP de Google.
seo-title: Configuraciones seguras y SameSite
title: Configuraciones seguras y SameSite
translation-type: ht
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: ht
source-wordcount: '174'
ht-degree: 100%

---


# Configuraciones seguras y SameSite

Esta configuración le permite cambiar la configuración de las cookies y permitir [cookies AMCV](../../introduction/cookies.md) en las páginas AMP de Google.

El servicio de ID de visitante de Adobe establece cookies de ECID con la configuración predeterminada del explorador `SameSite = Lax`, que no es accesible si la página se carga en un iframe como puede ser una página de AMP de Google. Para acceder a las cookies de ECID, utilice las siguientes configuraciones para actualizar el ajuste SameSite a `SameSite = None`.

>[!NOTE]
>
>Al aplicar `SameSite = None`, las cookies deben establecerse en `Secure` para que los datos solo puedan pasarse a través de conexiones HTTPS.

**Implementación**:

Si utiliza Adobe Experience Platform Launch, actualice la extensión de Experience Cloud ID a la versión 5.1.0, y configure `secureCookie: true` y `sameSiteCookie: none`.

Si no utiliza Experience Platform Launch, actualice a la biblioteca de Visitor 5.1.0 más reciente y aplique la configuración que se indica a continuación cuando inicie la instancia de Visitor:

**Ejemplo de código**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
