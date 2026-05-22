---
description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitor.
keywords: Servicio de ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 226
ht-degree: 96%

---

# getInstance{#getinstance}

getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitor.

**Sintaxis**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*No* cree instancias de la función Visitante con `var visitor = new Visitor`. Debe utilizar la función de llamada adecuada que se indica aquí. Se aplica a la [!UICONTROL VisitorAPI.js] biblioteca de códigos v3.0 o posterior.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Si `getInstance` no encuentra una instancia existente, se crea y se devuelve una instancia nueva. Esto es similar a la función [`s_gi()` ](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=es) en [!DNL AppMeasurement].

**Uso común**

La API del servicio de ID de [!DNL Experience Cloud] mantiene una lista de todas las instancias creadas para cada [!DNL Adobe Experience Cloud] ID de organización de. Si la aplicación que utiliza la API de servicio de ID no pasa una referencia a la instancia, puede encontrar dicha instancia llamando a `getInstance` en lugar de crear una nueva. Esto también es compatible con varias instancias para distintas organizaciones en la misma página web o aplicación.

Esta posibilidad es útil para las aplicaciones que no tengan una `init` fase clara, pero necesiten llamar a la API de visitante en varios lugares. Puede llamar a `getInstance` en todos esos lugares, y el primero en ejecutar creará la instancia. La instancia existente se devolverá mediante llamadas subsiguientes.

