---
description: Esta función se ha diseñado principalmente para ayudar a los clientes de A4T a solucionar los problemas relacionados con el uso de ID en páginas o pantallas únicas, o bien en aplicaciones.
keywords: Servicio de ID
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '374'
ht-degree: 100%

---

# resetState{#resetstate}

Esta función se ha diseñado principalmente para ayudar a los clientes de A4T a solucionar los problemas relacionados con el uso de ID en páginas o pantallas únicas, o bien en aplicaciones.

## Casos de uso {#section-840b88a5cdb042488b340cad5d7b22a5}

Como cliente de A4T que utiliza el servicio de ID, puede que desee utilizar la función `visitor.resetState()` cuando necesite:

* Para pasar un ID de datos suplementarios (SDID) o cualquier otro ID de una página o pantalla a otra mediante una redirección. Por lo general, el servicio de ID no pasa este ID sin esta función.
* Utilice código que solo actualice secciones específicas de una página o aplicación a través de llamadas Ajax y desee rastrear esas acciones. Por ejemplo, supongamos que tiene una página en la que al hacer clic en un objeto solo se carga o cambia una sección especial. En este caso, el servicio de ID no puede solicitar un ID diferente a menos que se vuelva a cargar la página. Sin embargo, con `visitor.resetState()`, puede solicitar un nuevo ID con estas condiciones.

Consulte los ejemplos de código que aparecen a continuación.

## Sintaxis {#section-9e63503e178f4be28ac850abf44d6d91}

**Sintaxis:** ` visitor.resetState( *`state`*);`

## Ejemplos de código {#section-d75b211bb4ea473887eb284de2ad838b}

La implementación del servicio de ID afecta a cómo utilizaría esta función. Consulte la tabla siguiente para ver ejemplos.

**Implementación del lado del servidor**

Una implementación del lado del servidor va dirigida a los clientes de A4T con implementaciones mixtas del lado del servidor y del cliente de [!DNL Target], [!DNL Analytics] y el servicio de ID. Si ha configurado el servicio de ID con este método, todo lo que debe hacer es agregar `visitor.resetState()` a la página. Las llamadas al servicio de ID devolverán un nuevo estado de servidor e ID inmediatamente.

**Implementación no estándar** (con ID)

Si ha configurado el servicio de ID con una [implementación no estándar](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), debe configurar un objeto de variable para mantener el SDID (u otros ID) que desee pasar con `visitor.resetState()`. Como se muestra a continuación, esto incluiría su [ID de organización](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) y el ID que desea pasar. Su código podría ser similar al del siguiente ejemplo.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Implementación no estándar** (sin pasar un ID)

En este caso, se puede utilizar `visitor.resetState()` para generar un nuevo ID. Esto puede resultar útil en una aplicación de una sola página cuando un usuario navega a una nueva pantalla sin actualizar la página y necesita un nuevo ID.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Administrador dinámico de etiquetas (DTM)**

Actualmente, no hay ninguna ruta de configuración de DTM para `visitor.resetState()`.
