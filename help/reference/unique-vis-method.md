---
title: Identificación de visitantes únicos
description: Documentación para Adobe ECID (servicio de ID)
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identificación de visitantes únicos

El método para identificar visitantes únicos entre contextos múltiples incluye una secuencia priorizada para garantizar la precisión en esta determinación. La siguiente tabla muestra esta secuencia con prioridad:


 
| Pedido utilizado| Parámetro de consulta (método de recopilación)| valor de columna post_visid_type| Presente cuando ||—|—|—|— || 1 |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.visitorID está establecido.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid (AMCV_ cookie configurada por Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | El explorador del visitante acepta cookies (de origen) y se implementa Identity Service. || 4 |[fid (cookie de reserva en H.25.3 o posterior, o AppMeasurement para JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | El explorador del visitante acepta cookies (de origen). || 5 | Encabezado[de suscriptor móvil](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)HTTP | 2 | El dispositivo se reconoce como dispositivo móvil. || 6 | Dirección[IP, agente de usuario, dirección](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)IP de puerta de enlace | 1 | El explorador del visitante no acepta cookies. |


Para obtener información sobre cómo se informan los visitantes únicos, consulte Visitantes [únicos en Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
