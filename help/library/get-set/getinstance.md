---
description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Esto es necesario para inicializar el objeto de ID de visitante proporcionado a AppMeasurement mediante s.visitor.
keywords: Servicio de ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

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
>*No* cree instancias de la función Visitante con `var visitor = new Visitor`. Debe utilizar la función de llamada adecuada que se indica aquí. Se aplica a la biblioteca de códigos 3.0 o posterior de [!UICONTROL VisitorAPI.js].

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
