---
description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitante.
keywords: ID Service
seo-description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitante.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getInstance{#getinstance}

getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitante.

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
>*No* cree instancias de la función Visitante con `var visitor = new Visitor`. Debe utilizar la función de llamada adecuada que se indica aquí. Applies to [!UICONTROL VisitorAPI.js] code library v3.0 or higher.

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

Si `getInstance` no encuentra una instancia existente, se crea y se devuelve una instancia nueva. Esto es similar a la [ función `s_gi()` en ](https://docs.adobe.com/content/help/en/analytics/implementation/vars/functions/s-gi.html) [!DNL AppMeasurement].

**Uso común**

La API del servicio de ID de [!DNL Experience Cloud] mantiene una lista de todas las instancias creadas para cada [!DNL Adobe Experience Cloud] ID de organización de. Si la aplicación que utiliza la API de servicio de ID no pasa una referencia a la instancia, puede encontrar dicha instancia llamando a `getInstance` en lugar de crear una nueva. Esto también es compatible con varias instancias para distintas organizaciones en la misma página web o aplicación.

Esta posibilidad es útil para las aplicaciones que no tengan una `init` fase clara, pero necesiten llamar a la API de visitante en varios lugares. Puede llamar a `getInstance` en todos esos lugares, y el primero en ejecutar creará la instancia. La instancia existente se devolverá mediante llamadas subsiguientes.
