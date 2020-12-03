---
description: API para la biblioteca de Opt-in y referencia de ajustes de configuración.
seo-description: API para la biblioteca de Opt-in y referencia de ajustes de configuración.
seo-title: Referencia de Opt-in
title: Referencia de Opt-in
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 74%

---


# Referencia de Opt-in{#opt-in-reference}

API para la biblioteca de Opt-in y referencia de ajustes de configuración.

La configuración de consentimiento se proporciona a las funciones de Opt-in como categorías:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Parámetros de configuración de Opt-in {#section-d66018342baf401389f248bb381becbf}

Esta sección trata sobre el uso de la API para configurar Opt-in. Buena parte de la configuración y la implementación se pueden realizar utilizando la extensión de Experience Platform Launch.

Se proporcionan configuraciones de Opt-in en la función `getInstance()` de Visitor JavaScript, que crea una instancia del objeto global `adobe`. A continuación se enumeran las configuraciones de Visitor JS relacionadas con el servicio Opt-in.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**::

Si es false, indica que los visitantes no necesitan adhesión. Da como resultado que el Experience Cloud cree cookies independientemente de las categorías adhesión o no. Esta configuración habilita o deshabilita holísticamente la inclusión.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Define qué categorías se aprueban o rechazan cuando el visitante todavía no ha establecido preferencias. Se las conoce como valores predeterminados de organización.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

Las preferencias explícitamente establecidas del visitante. Los permisos en esta configuración sobrescriben los valores predeterminados de organización (`previousPermissions` sobrescribe `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Habilita Opt-in para almacenar los permisos en una cookie de origen (dentro del dominio actual del cliente)

(Opcional) **`optInCookiesDomain (string)`**

Dominio o subdominio de origen a usar para la cookie de Opt-in (si `isOptInStorageEnabled` es “true”)

(Opcional) **`optInStorageExpiry (integer)`**

Número de segundos para anular la caducidad predeterminada de 13 meses

## Cambios en los parámetros de consentimiento {#section-c3d85403ff0d4394bd775c39f3d001fc}

En cualquier momento durante su experiencia en el sitio, un visitante puede establecer las preferencias por primera vez o puede cambiar sus preferencias usando su CMP. Una vez inicializada la Visitante JS con la configuración inicial, los permisos del visitante se pueden cambiar con las siguientes funciones:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Función que aprueba o incluye al visitante en todas las categorías de una lista. Para obtener más información sobre el parámetro mustWaitForComplete, consulte Flujo de trabajo [de inclusión](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Función que rechaza o excluye al visitante de todas las categorías especificadas.

**`adobe.optIn.approveAll()`**::

Si la solicitud de permiso de creación para su sitio está redactada de tal modo que un manto de visitante concede o deniega permiso a su sitio para la creación de cookies, utilice `approveAll()` o `denyAll()`, en función de su respuesta.

**`adobe.optIn.denyAll()`**::

Si la solicitud de permiso de creación para su sitio está redactada de tal modo que un manto de visitante concede o deniega permiso a su sitio para la creación de cookies, utilice `approveAll()` o `denyAll()`, en función de la respuesta.

## Parámetros de los flujos de trabajo de inclusión {#section-2c5adfa5459c4e72b96d2693123a53c2}

Opt-in es compatible con un flujo de trabajo en el que los permisos pueden recabarse a lo largo de más de un ciclo de solicitud, por ejemplo, cuando las preferencias se conceden de una en una. Si utiliza las funciones siguientes y proporciona *true* como valor de `shouldWaitForComplete`, su solución puede recabar el consentimiento para una solución o un subconjunto de las categorías totales y, a continuación, recabarlo para la solución o el subconjunto de categorías siguientes. Comenzando por la primera llamada, la propiedad `adobe.optIn.status` estará pendiente hasta que se realice una llamada a `adobe.optIn.complete()` al final del flujo. Una vez realizada la llamada, el estado se establecerá en *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Función que aprueba o incluye al visitante en todas las categorías de una lista.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Función que rechaza o excluye al visitante de todas las categorías especificadas.

`adobe.optIn.complete()`

Función que activa la agregación de las llamadas precedentes a approve() y deny() en una misma solicitud para establecer las preferencias de un visitante. Al suscribirse a los cambios en Opt-in —(consulte `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) a continuación—, su devolución de llamada solo se activa cuando se realiza una llamada a esta función.

## Parámetros de permisos de Opt-in de visitante {#section-7fe57279b5b44b4f8fe47e336df60155}

Recabe permisos de Opt-in para un visitante en cualquier momento mediante una de las funciones de permisos:

`adobe.optIn.permissions`

Un objeto que enumera todas las soluciones de Experience Cloud que, como categorías, el visitante ha concedido o rechazado.

`adobe.optIn.isApproved(categories)`

Si todas las categorías están aprobadas, esta función devuelve el valor “true”.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Recupere la lista de permisos de forma asíncrona. La llamada de retorno se realiza con la lista de permisos, una vez que se completa el proceso de concesión y denegación de permisos. Si se proporciona el valor *true* para `shouldAutoSubscribe`, la devolución de llamada se registra para cualquier cambio que se produzca en adelante en Opt-in. Las siguientes son propiedades de `adobe.OptIn`:

**`permissions`**

Un objeto que enumera todas las soluciones de Experience Cloud que, como categorías, el visitante ha concedido o rechazado. Ejemplo: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pendiente
* cambiado
* completo

**`doesOptInApply`**

“true” o “false”, según la configuración que haya proporcionado en la inicialización.

**`isPending`**

True o false, según el valor de estado. Los informes de inclusión verdaderos para esta propiedad para un visitante que aún no ha aceptado o denegado explícitamente el permiso

**`isComplete`**

True o false según el valor de estado. La inclusión podría informar de un valor falso para esta propiedad cuando se ha iniciado un consentimiento de estilo de flujo de trabajo pero no se ha completado.

## Métodos del objeto Opt-in {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: una o más categorías a aprobar. Por ejemplo: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (opcional) parámetro booleano, “false” de forma predeterminada. Si se pasa el valor “true”, Opt-in no completa el proceso de aprobación hasta que se realiza una llamada a `adobe.optIn.complete()`. Este proceso es similar a un flujo de trabajo.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Pase 1 o más categorías para comprobar si están aprobadas.
* Si no se pasa ninguna categoría, se marcan TODAS las categorías disponibles.

**`isApproved(categories)`**

Comprueba si el cliente ha aprobado una o más categorías.

**`isPreApproved(categories)`**

Comprueba si el cliente ha preaprobado una o más categorías. (Si se pasaron en el `preOptInApprovals` ajuste).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

Async API para recuperar la lista de permisos. La llamada de retorno se realiza con la lista de permisos, una vez que se completa el proceso de concesión y denegación de permisos. **:**`shouldAutoSubscribe` una utilidad de ayuda que suscribe automáticamente esta devolución de llamada a todos los eventos futuros. Es decir, la llamada de retorno se llamará cada vez que se Adhesión un activador de aprobación o denegación. De esta manera siempre se actualiza, sin suscribirse a los eventos.

**Ejemplo**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Utilícelo solo si ha pasado el `shouldWaitForComplete` parámetro para aprobar o denegar. Esta API completa el proceso de aprobación. Ejemplo: `adobe.optIn.complete()`.

**`approveAll()`:**

Aprueba todas las categorías existentes.

**`denyAll()`**

Deniega todas las categorías existentes.

## Eventos del objeto Opt-in {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

Completa activadores de evento una vez terminado el proceso de aprobación. Si realiza una llamada de aprobación/rechazo sin pasar `shouldWaitForComplete`, o `approveAll`/`denyAll`, este evento se activa. O bien, si se pasa `shouldWaitForComplete`, este evento se activa cuando se realiza una llamada a `complete`.

**Ejemplo**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
