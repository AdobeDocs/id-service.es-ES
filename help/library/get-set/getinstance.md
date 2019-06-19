---
description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Es necesario para inicializar el objeto de ID de visitante que se proporciona a AppMeasurement mediante s.visitor.
keywords: Servicio de ID
seo-description: getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Es necesario para inicializar el objeto de ID de visitante que se proporciona a AppMeasurement mediante s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-e 3 d 0-4 aab-b 935-566099 bdab 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getInstance{#getinstance}

getInstance devuelve un objeto de ID de visitante para el ID de organización de Experience Cloud especificado. Es necesario para inicializar el objeto de ID de visitante que se proporciona a AppMeasurement mediante s.visitor.

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
>*No* cree instancias de la función Visitante con `var visitor = new Visitor`. Debe utilizar la función de llamada adecuada que se indica aquí. Se aplica a la biblioteca de códigos [!DNL VisitorAPI.js] v3.0 o posterior.

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

Si `getInstance` no encuentra una instancia existente, se crea y se devuelve una instancia nueva. Esto es similar a [`s_gi()` la función ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Uso común**

La API de servicio [!DNL Experience Cloud] de ID mantiene una lista de todas las instancias creadas para cada ID [!DNL Adobe Experience Cloud] de organización. Si la aplicación que utiliza la API de servicio de ID no pasa una referencia a la instancia, puede encontrar dicha instancia llamando a `getInstance` en lugar de crear una nueva. Esto también es compatible con varias instancias para distintas organizaciones en la misma página web o aplicación.

Esta posibilidad es útil para las aplicaciones que no tengan una fase `init` clara, pero necesiten llamar a la API de visitante en varios lugares. Puede llamar a `getInstance` en todos esos lugares, y el primero en ejecutar creará la instancia. La instancia existente se devolverá mediante llamadas subsiguientes.
