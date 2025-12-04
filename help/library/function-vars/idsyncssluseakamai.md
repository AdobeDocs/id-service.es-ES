---
description: Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.
keywords: Servicio de ID
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.

La `idSyncSSLUseAkamai` configuración se habilita de forma independiente para cada socio.

**Sintaxis:** `idSyncSSLUseAkamai: true`

**Ejemplo de código**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

