---
description: Notas de la versión y actualizaciones para 2015.
keywords: Servicio de ID
seo-description: Notas de la versión y actualizaciones para 2015.
seo-title: Notas de la versión 2015
title: Notas de la versión 2015
uuid: 49423699-1 e 0 f -49 e 4-9135-2 ae 84 b 4 f 92 df
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Notas de la versión 2015 {#release-notes}

Notas de la versión y actualizaciones para 2015.

## Versión 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Noviembre de 2015

La Ley de protección de la privacidad infantil en línea (Children&#39;s Online Privacy Protection Act, COPPA) prohíbe la recopilación en línea de información personal de niños menores de 13 años sin previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de ID de [!DNL Experience Cloud] que impida la instalación de cookies en el dominio de terceros de un navegador. Consulte [Compatibilidad con COPPA en el servicio de identidad de Experience Platform](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Para la versión 1.5.3 o superior.

## Versión 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Septiembre de 2015

* Se ha corregido un error del explorador Safari que impedía que los servicios de sincronización funcionaran si los usuarios bloqueaban las cookies de terceros. (AAM-20764)
* Las llamadas al servicio de ID ahora incluyen el ID de versión en el `d_visid_ver=` parámetro. El ID devuelto ayuda a los equipos internos en la solución de problemas y los problemas de soporte. (AAM-20824)

## Versión 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Agosto de 2015

* Se ha corregido un error para evitar que el servicio de ID solicitara un iframe en caso de que no hubiera datos para sincronizar o entregar. (AAM-20164)
* Se ha corregido un problema que impedía que el servicio de ID estableciera correctamente una cookie de dominio superior de varias partes. Por ejemplo, si tiene un dominio como `my_company.co.uk`, en determinadas circunstancias, el servicio de ID establecería una cookie solo en `co.uk`. (AN-104683)

   Esto solo afectaba a algunos clientes que cumplían *todos* estos criterios:

   * Usaban el servicio de ID.
   * Se había habilitado un [periodo de gracia](../reference/analytics-reference/grace-period.md) *o* se usaban cookies propias y los clientes habían bloqueado las cookies de terceros.

   * Tenían páginas con dominios de nivel superior en varias partes.

Las revisiones de documentación de esta versión incluyen:

* [Métodos de API y Biblioteca de códigos](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Contenido y texto reorganizados. En la mayoría de los casos, cada método obtiene su propia página.
* [Requisitos del servicio de identidad de la plataforma de experiencia](../reference/requirements.md): Contenido revisado y texto reorganizado.

## Versión 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Julio de 2015

El servicio de ID de [!DNL Experience Cloud] admite varios ID y estados de autenticación. Este cambio elimina también la compatibilidad obsoleta con las asignaciones de DPID de [!DNL Audience Manager] a los ID de usuario utilizados por la función `setCustomerIDs`. Consulte [ID de cliente y estados de autenticación](../reference/authenticated-state.md)

## Versión 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mayo de 2015

En la versión 1.4, el método preferido para establecer la configuración es pasar un objeto de configuración como el segundo parámetro de la función `Visitor.getInstance`..

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Consulte [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Versión 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Febrero de 2015

Se ha corregido la administración de tiempos de espera en solicitudes para AAM Blob y los consejos de ubicación. Ahora, en un tiempo de espera, el sistema dejará en blanco correctamente los campos correspondientes de la página actual y se realizarán todas las rellamadas. El tiempo de espera se trata como una condición de error, de modo que lo volverá a intentar en la página siguiente. (AN-94473, AN-94474)

## Versión 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Enero de 2015

Se modificó `<head>/<body>` la búsqueda de etiquetas para contenedor `<script>` de etiquetas de solicitud JSONP, así como la creación de `<script>` la etiqueta para tener en cuenta las diferentes implementaciones DOM (HTML vs. XHTML) con posibles configuraciones de distinción entre mayúsculas y minúsculas. (AN-9355)
