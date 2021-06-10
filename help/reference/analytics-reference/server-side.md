---
description: En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).
keywords: Servicio de ID
title: Implementación del lado del servidor combinada con JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Implementación del lado del servidor combinada con JavaScript {#server-side-implementation-mixed-with-javascript}

En algunas implementaciones, los ID de visitante se pasan de JavaScript a un servidor para que este pueda enviar los eventos de Analytics adicionales (como las compras).

La API del servicio de ID proporciona los métodos [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) y [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) para recuperar los valores de ID que se pueden pasar al servidor.

Asegúrese de comprobar la existencia del ID de visitante de Experience Cloud y el ID de visitante de Analytics y de enviarlos (si están presentes) para garantizar que los datos que se envíen se asocien al perfil del visitante de Analytics existente.

>[!IMPORTANT]
>
>AppMeasurement para Java todavía no es compatible con el servicio de identidad de Experience Cloud.

## API de inserción de datos {#section-955ce7664a4646d38b3005cb2df40baf}

Incluya el ID de visitante de Analytics (si está configurado) en el elemento `<visitorID>`.

Incluya el ID de visitante de Experience Cloud en el elemento `<marketingCloudVisitorID>`.

Consulte [Etiquetas XML admitidas](https://www.adobe.io).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

El servicio de identidad de Experience Cloud todavía no es compatible con AppMeasurement para Java.
