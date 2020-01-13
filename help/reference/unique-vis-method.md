---
title: Identificación de visitantes únicos
description: Documentación de Adobe ECID (servicio de ID)
translation-type: ht
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identificación de visitantes únicos

El método para identificar visitantes únicos entre varios contextos incluye una secuencia priorizada para garantizar la exactitud en esta determinación. La tabla siguiente muestra esta secuencia priorizada:


 
| Pedido utilizado | Parámetro de consulta (método de colección) | valor de columna post_visid_type| Presente cuando se establece |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/es_ES/sc/implement/visid_custom.html) | 0 |s.visitorID.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/es_ES/sc/implement/visid_analytics.html) | 3 |El visitante tenía una cookie s_vi existente antes de que se implementara el servicio de ID del visitante o de configurar un [periodo de gracia](https://marketing.adobe.com/resources/help/es_ES/mcvid/mcvid_grace_period.html) del ID del visitante. |
| 3 | [mid (AMCV_ cookie set by Identity Service)](https://marketing.adobe.com/resources/help/es_ES/mcvid/) | 5 | El explorador del visitante acepta cookies (propias) y se implementa Identity Service. |
| 4 | [fid (cookie de reserva en H.25.3 o posterior, o AppMeasurement para JavaScript)](https://marketing.adobe.com/resources/help/es_ES/sc/implement/visid_fallback.html) | 4 | El explorador del visitante acepta cookies (propias). |
| 5 | [Encabezado de suscriptor móvil HTTP](https://marketing.adobe.com/resources/help/es_ES/sc/implement/visid_mobile.html) | 2 | El dispositivo se reconoce como dispositivo móvil. |
| 6 | [Dirección IP, agente de usuario, dirección IP de puerta de enlace](https://marketing.adobe.com/resources/help/es_ES/sc/implement/visid_fallback.html) | 1 | El explorador del visitante no acepta cookies. |


Para obtener información sobre cómo se informan los visitantes únicos, consulte [Visitantes únicos en Analytics](https://docs.adobe.com/content/help/es-ES/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
