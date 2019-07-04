---
description: En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).
keywords: Servicio de ID
seo-description: En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).
seo-title: Implementación del lado del servidor combinada con JavaScript
title: Implementación del lado del servidor combinada con JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementación del lado del servidor combinada con JavaScript {#server-side-implementation-mixed-with-javascript}

En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).

La API de servicio de ID proporciona métodos, [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) y [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) para recuperar los valores de ID que luego puedan pasarse al servidor.

Asegúrese de comprobar la existencia del ID de visitante de Experience Cloud y el ID de visitante de Analytics y de enviarlos (si están presentes) para garantizar que los datos que se envíen se asocien al perfil del visitante de Analytics existente.

>[!IMPORTANT]
>
>AppMeasurement para Java todavía no admite el servicio Experience Cloud ID.

## API de inserción de datos {#section-955ce7664a4646d38b3005cb2df40baf}

Incluya el ID de visitante de Analytics (si está configurado) en el elemento `<visitorID>`.

Incluya el ID de visitante de Experience Cloud en el elemento `<marketingCloudVisitorID>`.

Consulte [Etiquetas XML admitidas](https://marketing.adobe.com/developer/es_ES/documentation/data-insertion/r-supported-tags).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

El servicio Experience Cloud ID todavía no se admite en AppMeasurement para Java.
