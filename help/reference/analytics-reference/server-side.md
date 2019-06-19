---
description: En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).
keywords: Servicio de ID
seo-description: En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).
seo-title: Implementación del lado del servidor combinada con JavaScript
title: Implementación del lado del servidor combinada con JavaScript
uuid: 256 ea 0 e 7-1 eb 4-4 c 92-9 a 7 e-f 61 cb 1 ed 13 c 7
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementación del lado del servidor combinada con JavaScript {#server-side-implementation-mixed-with-javascript}

En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).

La API de servicio de ID proporciona métodos, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) y [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) para recuperar los valores de ID que luego puedan pasarse al servidor.

Asegúrese de comprobar la existencia del ID de visitante de Experience Cloud y el ID de visitante de Analytics y de enviarlos (si están presentes) para garantizar que los datos que se envíen se asocien al perfil del visitante de Analytics existente.

>[!IMPORTANT]
>
>Appmeasurement para Java no admite actualmente el servicio de identidad de Experience Platform.

## API de inserción de datos {#section-955ce7664a4646d38b3005cb2df40baf}

Incluya el ID de visitante de Analytics (si se ha configurado) en `<visitorID>` el elemento.

Incluya el ID de visitante de Experience Cloud en `<marketingCloudVisitorID>` el elemento.

Consulte [Etiquetas XML admitidas](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

El servicio de identidad de Experience Platform no se admite actualmente en appmeasurement para Java.
