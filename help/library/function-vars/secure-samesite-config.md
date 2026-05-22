---
description: Una configuración de ECID que puede usarse para permitir cookies AMCV en páginas de AMP de Google.
keywords: Servicio de ID
title: Configuraciones seguras y SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
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

