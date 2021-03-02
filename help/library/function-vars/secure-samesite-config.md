---
description: Una configuración dentro de ECID que puede utilizarse para admitir cookies AMCV en páginas AMP de Google.
keywords: Servicio de ID
seo-description: Una configuración dentro de ECID que puede utilizarse para admitir cookies AMCV en páginas AMP de Google.
seo-title: Configuraciones seguras y SameSite
title: Configuraciones seguras y SameSite
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# Configuraciones seguras y SameSite

Esta configuración le permite cambiar la configuración de las cookies y admitir [cookies AMCV](../../introduction/cookies.md) en las páginas AMP de Google.

El servicio de ID de visitante de Adobe establece cookies ECID con la configuración predeterminada del explorador `SameSite = Lax`, que es inaccesible si la página se carga en un iframe como una página de AMP de Google. Para acceder a las cookies ECID, utilice las siguientes configuraciones para actualizar la configuración SameSite a `SameSite = None`.

>[!NOTE]
>
>Al aplicar `SameSite = None`, las cookies deben configurarse como `Secure`, de modo que los datos solo puedan pasarse a través de conexiones HTTPS.

**Implementación**:

Si utiliza Adobe Experience Platform Launch, actualice la extensión Experience Cloud ID a la versión 5.1.0 y configure `secureCookie: true` y `sameSiteCookie: none`.

Si no utiliza Experience Platform Launch, actualice la biblioteca de Visitante 5.1.0 más reciente y siga las configuraciones a continuación, mientras inicia la instancia de Visitante:

**Ejemplo de código**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
