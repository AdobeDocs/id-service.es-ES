---
description: Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.
keywords: Servicio de ID
seo-description: Especifica si la plantilla de publicación de destino debería utilizar Akamai para conexiones HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

