---
description: Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.
keywords: Servicio de ID
seo-description: Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501 ccc 37-c 3 ab -4454-bfcf -3 e 3 c 3 e 8 ca 5 ca 3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.

La configuración `idSyncSSLUseAkamai` se habilita de forma independiente para cada socio.

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

