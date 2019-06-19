---
description: Implementar el servicio de selección como punto de referencia único utilizado por las soluciones de Experience Cloud (denominado Categorías en la inclusión) para determinar si se crean cookies en el dispositivo de un visitante.
seo-description: Implementar el servicio de selección como punto de referencia único utilizado por las soluciones de Experience Cloud (denominado Categorías en la inclusión) para determinar si se crean cookies en el dispositivo de un visitante.
seo-title: Configuración del servicio de selección
title: Configuración del servicio de selección
uuid: f 1 c 27139-cef 2-4122-af 12-c 839 cfc 82 e 6 e
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# Configuración del servicio de selección{#setting-up-opt-in-service}

Implementar el servicio de selección como punto de referencia único utilizado por las soluciones de Experience Cloud (denominado Categorías en la inclusión) para determinar si se crean cookies en el dispositivo de un visitante.

El servicio de selección es una biblioteca JavaScript compilada con Experience Cloud ID (ECID) y existe en el JS de visitante del `adobe` objeto global como `adobe.optIn` objeto. El servicio de inclusión instalado le permite especificar si un visitante puede participar en soluciones de Adobe a la vez o presentar soluciones en secuencia para obtener permiso para cada uno. La función de administración de consentimiento del servicio de selección le permite implementar con varias configuraciones para sus requisitos de privacidad específicos.

El servicio de selección permite especificar si un visitante puede activar las soluciones de Adobe a la vez o presentar las soluciones en secuencia para el permiso de cada uno. Una vez que el cliente completa y registra el proceso de aprobación, todas las soluciones de Adobe pueden recuperar las aprobaciones de visitante de CMP para responder con llamadas de consentimiento relacionadas.

## Requisitos previos {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versión 4.0.

   [Descargue](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la versión más reciente de ECID.

1. Bibliotecas de soporte:

   * ECID 4.0 o posterior
   * AppMeasurement 2.11 o posterior
   * DIL 9.0
   * AT.js versión 1.7.0
   * Extensión AT.js para Launch versión 9.0
   * Para Analytics, AppMeasurement 2.11 con la extensión 1.6
   * Para Target, la extensión 0.9.1

1. Conozca en profundidad el marco de gestión del consentimiento que va a utilizar con Opt-in y entienda cualquier requisito previo adicional.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Los requisitos de privacidad de su empresa dependerán de cómo elija satisfacer el cumplimiento del RGPD. Debe saber qué bibliotecas pueden utilizar los equipos de privacidad de su empresa previamente al consentimiento.

Si utiliza [Launch, de Adobe](https://docs.adobelaunch.com/), aproveche la [Extensión de inclusión](../../implementation-guides/opt-in-service/launch.md) para configurar el servicio de selección.

## Categorías de inclusión {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Las preferencias de Opt-in de un visitante dependen de la solución de Adobe Experience Cloud, representándose cada solución mediante una categoría. Las categorías las proporciona el objeto `adobe.OptInCategories`, donde, por ejemplo, el componente ECID es referido como `adobe.OptInCategories`. `ECID`. La siguiente es la definición de `adobe.OptInCategories`:

La configuración de Opt-in se mantiene por categoría, estando cada solución de Experience Cloud representada por una categoría:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

El servicio de selección le permite establecer las preferencias de permisos de los visitantes por cada solución de Adobe utilizada en el sitio. Incluye una biblioteca para guardar la configuración de un visitante para cada categoría aprobada y admite un flujo secuencial, por el que el proceso de aprobación recibe una a una las preferencias de “confirmación” o “rechazo” para cada categoría. Puede establecer soluciones/categorías para realizar la inclusión en bloque o para cada una de las soluciones.
Todas las bibliotecas de Adobe de cliente dependen del servicio de inclusión y no generarán cookies, a menos que se haya concedido permiso a la solución. Opt-in ofrece diversos enfoques para proporcionar y actualizar la configuración de consentimiento del visitante actual. Esta sección proporciona ejemplos para establecer las preferencias de servicio de selección. Consulte la Referencia de API [de inclusión](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obtener una lista completa de funciones y parámetros.

Las configuraciones de servicio de inclusión se proporcionan en la función JS `getInstance()` de visitante que crea una instancia del `adobe` objeto global. A continuación se enumeran las opciones [de configuración de JS del visitante](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) para el servicio de inclusión.

**Configuración de inclusión de ejemplo en inicialización del`Visitor`objeto global**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Gestión de cambios en el consentimiento**

En cualquier momento durante su experiencia en el sitio, un visitante puede establecer preferencias por primera vez o puede cambiar sus preferencias mediante CMP. Una vez que Visitor JS se ha inicializado con su configuración inicial, es posible cambiar los permisos del visitante. Consulte [Cambios en el consentimiento](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) para obtener una lista de administración de funciones de consentimiento.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Flujos de trabajo de selección {#section-70cd243dec834c8ea096488640ae20a5}

El servicio de inclusión admite un flujo de trabajo donde los permisos pueden recopilarse en más de un ciclo de solicitud y las preferencias se proporcionan de uno en uno. Si utiliza las funciones siguientes y proporciona *true* como valor de `shouldWaitForComplete`, su solución puede recabar el consentimiento para una solución o un subconjunto de las categorías totales y, a continuación, recabarlo para la solución o el subconjunto de categorías siguientes. A partir de la primera llamada, la `adobe.optIn.status` propiedad *estará pendiente* hasta `adobe.optIn.complete()` que se llame al final del flujo. Una vez realizada la llamada, el estado se establecerá en *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consulte [Configuración de configuración del flujo de trabajo](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Inspeccione los permisos de Opt-in del visitante {#section-f136a9024e054d84881e6667fb7c94eb}

A medida que los visitantes realicen cambios en sus permisos, necesitará conocer los permisos resultantes para sincronizar su almacén de consentimiento con los cambios realizados en el servicio de inclusión. Inspeccione las preferencias del visitante mediante las [funciones de permisos](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), como por ejemplo:

**fetchPermissions sample**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

Consulte [la documentación de la API](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obtener más información sobre estas funciones, propiedades y configuraciones mencionadas en este documento.

## Almacenamiento de preferencias de visitantes {#section-ef2884ae67e34879bf7c7c3372706c9f}

El servicio de selección proporciona una opción para almacenar las preferencias de consentimiento adaptadas a un entorno de desarrollo o un entorno en el que no es viable utilizar una CRM. Al especificar la propiedad configuration `isOptInStorageEnabled` como *true* , se activa el servicio de inclusión para crear una cookie en el sistema del visitante dentro de su dominio.

El objeto `adobe.optIn` carece de estado y no proporciona ningún mecanismo de almacenamiento. Está pensado para permitirle gestionar la configuración de consentimiento de Adobe en su plataforma de gestión del consentimiento (CMP) existente, si es que esta permite el almacenamiento de datos personalizados. También puede almacenar las preferencias de visitante en una cookie en el navegador del visitante. Tiene dos opciones para proporcionar las preferencias del usuario al servicio de selección:

* Si la solución de persistencia de consentimiento, tanto si se trata de una CMP como de una cookie en el navegador del visitante, permite recuperar las preferencias de los visitantes, puede proporcionarlas al servicio de selección durante la inicialización del visitante.
* Sin embargo, si la recuperación puede ser un proceso largo o si lo hace mejor como proceso asincrónico, puede utilizar `approve()` la función del servicio para proporcionar dicha configuración una vez que se hayan cargado correctamente.

