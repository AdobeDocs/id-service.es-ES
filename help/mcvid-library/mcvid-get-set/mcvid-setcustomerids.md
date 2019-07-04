---
description: setCustomerIDs establece una o más parejas de valor clave que definen los ID de cliente y su estado de autenticación.
keywords: Servicio de ID
seo-description: setCustomerIDs establece una o más parejas de valor clave que definen los ID de cliente y su estado de autenticación.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs establece una o más parejas de valor clave que definen los ID de cliente y su estado de autenticación.

**Sintaxis:** `visitor.setCustomerIDs()`

Puede obtener ID sencillos o múltiples, como se indica en la muestra de código siguiente. Consulte [ID de cliente y estados de autenticación](../../mcvid-reference/mcvid-authenticated-state.md) para obtener más información y ejemplos.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

