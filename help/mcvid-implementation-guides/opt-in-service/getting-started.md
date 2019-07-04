---
description: Implemente el servicio de inclusión (Opt-in) como el único punto de referencia que utilizan las soluciones de Experience Cloud (denominadas “categorías” en Opt-in) para determinar si se crean o no cookies en el dispositivo de un visitante.
seo-description: Implemente el servicio de inclusión (Opt-in) como el único punto de referencia que utilizan las soluciones de Experience Cloud (denominadas “categorías” en Opt-in) para determinar si se crean o no cookies en el dispositivo de un visitante.
seo-title: Configuración del servicio de inclusión (Opt-in)
title: Configuración del servicio de inclusión (Opt-in)
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
translation-type: ht
source-git-commit: ae65e9c7da5ac9cbe22de3f956bcd7cbef2052a7

---


# Configuración del servicio de inclusión (Opt-in){#setting-up-opt-in-service}

Implemente el servicio de inclusión (Opt-in) como el único punto de referencia que utilizan las soluciones de Experience Cloud (denominadas “categorías” en Opt-in) para determinar si se crean o no cookies en el dispositivo de un visitante.

El servicio de inclusión (Opt-in) es una biblioteca JavaScript incluida con [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/es_ES/mcvid/) y existe en el JS de visitante del objeto global de `adobe` como el objeto `adobe.optIn`. El servicio de inclusión (Opt-in) instalado le permite especificar si un visitante puede incluirse en las soluciones de Adobe de una sola vez, o si se le van presentando las soluciones una tras otra para que vaya aprobando los permisos. La función de gestión del consentimiento del servicio de inclusión (Opt-in) le permite implementar distintas configuraciones, según sus requisitos específicos de privacidad.

El servicio Opt-in le permite especificar si un visitante puede incluirse en las soluciones de Adobe de una sola vez, o si se le van presentando las soluciones una tras otra para que vaya aprobando los permisos. Una vez que el cliente completa y registra el proceso de aprobación, todas las soluciones de Adobe pueden recuperar las aprobaciones de visitante de CMP para responder con llamadas de consentimiento relacionadas.

## Requisitos previos {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versión 4.0.

   [Descargar](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la versión de ECID más reciente.

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

Si utiliza [Adobe Launch](https://docs.adobelaunch.com/), aproveche la [extensión de inclusión Opt-in](../../mcvid-implementation-guides/opt-in-service/launch.md) para configurar el servicio de inclusión (Opt-in).

## Categorías de Opt-in {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Las preferencias de Opt-in de un visitante dependen de la solución de Adobe Experience Cloud, representándose cada solución mediante una categoría. Las categorías las proporciona el `adobe.OptInCategories` objeto, donde, por ejemplo, el componente ECID es referido como `adobe.OptInCategories`. `ECID`. La siguiente es la definición de `adobe.OptInCategories`:

La configuración de Opt-in se mantiene por categoría, estando cada solución de Experience Cloud representada por una categoría:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

El servicio Opt-in le permite establecer las preferencias de permiso de los visitantes para cada solución de Adobe que se emplee en el sitio. Incluye una biblioteca para guardar la configuración de un visitante para cada categoría aprobada y admite un flujo secuencial, por el que el proceso de aprobación recibe una a una las preferencias de “confirmación” o “rechazo” para cada categoría. Puede establecer soluciones/categorías para realizar la inclusión en bloque o para cada una de las soluciones. 
Las bibliotecas del lado del cliente de todas las soluciones de Adobe dependen del servicio Opt-in y no generarán cookies salvo que la solución haya obtenido permiso. Opt-in ofrece diversos enfoques para proporcionar y actualizar la configuración de consentimiento del visitante actual. Esta sección incluye ejemplos de cómo se establecen las preferencias del servicio Opt-in. Consulte la [Referencia de la API Opt-in](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obtener una lista completa de funciones y parámetros.

Se proporcionan configuraciones del servicio Opt-in en la `getInstance()` función de Visitor JS, que crea una instancia del `adobe` objeto global. A continuación se enumeran los [ajustes de configuración](../../mcvid-implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) de Visitor JS para el servicio Opt-in.

**Ejemplo de configuración de Opt-in en la inicialización del`Visitor`objeto global**

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

En cualquier momento durante su experiencia en el sitio, un visitante puede establecer preferencias por primera vez o puede cambiar sus preferencias mediante CMP. Una vez que Visitor JS se ha inicializado con su configuración inicial, es posible cambiar los permisos del visitante. Consulte [Cambios en el consentimiento](../../mcvid-implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) para ver una lista de funciones de gestión del consentimiento.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Flujos de trabajo de Opt-in {#section-70cd243dec834c8ea096488640ae20a5}

El servicio Opt-in es compatible con un flujo de trabajo en el que los permisos pueden recabarse a lo largo de más de un ciclo de solicitud y en el que las preferencias se conceden de una en una. Si utiliza las funciones siguientes y proporciona *true* como valor de `shouldWaitForComplete`, su solución puede recabar el consentimiento para una solución o un subconjunto de las categorías totales y, a continuación, recabarlo para la solución o el subconjunto de categorías siguientes. Comenzando por la primera llamada, la propiedad `adobe.optIn.status` estará en estado *pending* hasta que se realice una llamada a `adobe.optIn.complete()` al final del flujo. Una vez realizada la llamada, el estado se establecerá en *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consulte [Establecer una configuración del flujo de trabajo](../../mcvid-implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)

## Inspeccione los permisos de Opt-in del visitante {#section-f136a9024e054d84881e6667fb7c94eb}

A medida que los visitantes realicen cambios en sus permisos, necesitará conocer los permisos resultantes para sincronizar el almacén de consentimiento con los cambios realizados en el servicio Opt-in. Inspeccione las preferencias del visitante mediante las [funciones de permisos](../../mcvid-implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), como por ejemplo:

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

Consulte [la documentación de la API](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obtener más información sobre estas funciones, propiedades y configuraciones mencionadas en este documento.

## Conservar las preferencias de los visitantes{#section-ef2884ae67e34879bf7c7c3372706c9f}

El servicio Opt-in incluye una opción de almacenamiento de las preferencias de consentimiento adecuada para un entorno de desarrollo, o uno en el que no sea factible el uso de un CRM. Si la propiedad de configuración `isOptInStorageEnabled` se establece en *true*, el servicio Opt-in se activa para crear una cookie en el sistema del visitante dentro de su dominio.

El `adobe.optIn`objeto  carece de estado y no proporciona ningún mecanismo de almacenamiento. Está pensado para permitirle gestionar la configuración de consentimiento de Adobe en su plataforma de gestión del consentimiento (CMP) existente, si es que esta permite el almacenamiento de datos personalizados. También puede almacenar las preferencias de visitante en una cookie en el navegador del visitante. Tiene dos opciones para proporcionar las preferencias del usuario al servicio Opt-in:

* Si su solución de persistencia del consentimiento, ya sea una CMP o una cookie en el navegador del visitante, permite la oportuna recuperación de las preferencias de visitante, puede proporcionárselas al servicio Opt-in durante la inicialización del visitante.
* Sin embargo, si la recuperación puede ser un proceso prolongado o por cualquier otro motivo conviene realizarla como proceso asincrónico, puede utilizar la `approve()` función del servicio para proporcionar estos ajustes una vez cargados correctamente.

