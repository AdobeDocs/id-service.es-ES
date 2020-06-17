---
title: Identificación de visitantes únicos
description: Documentación de Adobe ECID (servicio de ID)
translation-type: ht
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---


# Identificación de visitantes únicos

El método para identificar visitantes únicos entre varios contextos incluye una secuencia priorizada para garantizar la exactitud en esta determinación. La tabla siguiente muestra esta secuencia priorizada:

| Pedido utilizado | Parámetro de consulta (método de colección) | valor de columna post_visid_type | Presente cuando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html)  | 0  | `s.visitorID` está configurado. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html)  | 3  | El visitante tenía una cookie s_vi existente antes de que se implementara el servicio de ID del visitante o de configurar un [periodo de gracia](https://docs.adobe.com/content/help/es-ES/id-service/using/reference/analytics-reference/grace-period.html) del ID del visitante.  |
|  3  | mid [AMCV_ cookie del Servicio de identidad](https://docs.adobe.com/content/help/es-ES/id-service/using/home.html)  |  5  |  El explorador del visitante acepta cookies (propias) y se implementa [!UICONTROL Identity Service].  |
|  4  | fid [cookie de seguridad en H.25.3 o posterior, o AppMeasurement para JavaScript](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html)  |  4  |  El explorador del visitante acepta cookies (de origen).  |
|  5  |  [Encabezado de suscriptor móvil HTTP](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html)  |  2  |  El dispositivo se reconoce como dispositivo móvil.  |
|  6  |  [Dirección IP, agente de usuario y dirección IP de puerta de enlace](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html)  |  1  |  El explorador del visitante no acepta cookies. |

Para obtener información sobre cómo se informan los visitantes únicos, consulte [Visitantes únicos en Analytics](https://docs.adobe.com/content/help/es-ES/analytics/components/metrics/unique-visitors.translate.html).
