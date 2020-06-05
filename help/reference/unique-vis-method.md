---
title: Identificación de visitantes únicos
description: Documentación de Adobe ECID (servicio de ID)
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 66%

---


# Identificación de visitantes únicos

El método para identificar visitantes únicos entre varios contextos incluye una secuencia priorizada para garantizar la exactitud en esta determinación. La tabla siguiente muestra esta secuencia priorizada:

| Pedido utilizado | Parámetro de Consulta (método de recopilación) | valor de columna post_visid_type | Presentar cuando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/es-ES/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` está configurado. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/es-ES/analytics/technotes/visitor-identification.html)  | 3  | El visitante tenía una cookie s_vi existente antes de que se implementara el servicio de ID del visitante o de configurar un [periodo de gracia](https://docs.adobe.com/content/help/es-ES/id-service/using/reference/analytics-reference/grace-period.html) del ID del visitante.  |
|  3  | cookie mid[AMCV_ establecida por Identity Service](https://docs.adobe.com/content/help/es-ES/id-service/using/home.html)  |  5  |  Visitor&#39;s browser accepts cookies (first-party), and the [!UICONTROL Identity Service] is deployed.  |
|  4  | fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://docs.adobe.com/content/help/es-ES/analytics/technotes/visitor-identification.html)  |  4  |  El explorador de Visitante acepta cookies (de origen).  |
|  5  |  [Encabezado de suscriptor móvil HTTP](https://docs.adobe.com/content/help/es-ES/analytics/technotes/visitor-identification.html)  |  2  |  El dispositivo se reconoce como un dispositivo móvil.  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/es-ES/analytics/technotes/visitor-identification.html)  |  1  |  El explorador de Visitante no acepta cookies. |

Para obtener información sobre cómo se informan los visitantes únicos, consulte [Visitantes únicos en Analytics](https://docs.adobe.com/content/help/es-ES/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
