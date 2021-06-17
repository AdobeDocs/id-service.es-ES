---
title: Identificación de visitantes únicos
description: Documentación de Adobe ECID (servicio de ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: ht
source-wordcount: '253'
ht-degree: 100%

---

# Identificación de visitantes únicos

El método para identificar visitantes únicos entre varios contextos incluye una secuencia priorizada para garantizar la exactitud en esta determinación. La tabla siguiente muestra esta secuencia priorizada:

| Pedido utilizado | Parámetro de consulta (método de colección) | valor de columna post_visid_type | Presente cuando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=es)  | 0  | `s.visitorID` está configurado. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=es#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | El visitante tenía una cookie s_vi existente antes de que se implementara el servicio de ID del visitante o de configurar un [periodo de gracia](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=es) del ID del visitante.  |
|  3  | mid [AMCV_ cookie del Servicio de identidad](../introduction/cookies.md)  |  5  |  El explorador del visitante acepta cookies (propias) y se implementa [!DNL Identity Service].  |
|  4  | fid [cookie de seguridad en H.25.3 o posterior, o AppMeasurement para JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=es#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  El explorador del visitante acepta cookies (de origen).  |
|  5  |  [Encabezado de suscriptor móvil HTTP](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=es)  |  2  |  El dispositivo se reconoce como dispositivo móvil.  |
|  6  |  [Dirección IP, agente de usuario y dirección IP de puerta de enlace](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=es)  |  1  |  El explorador del visitante no acepta cookies. |

{style=&quot;table-layout:auto&quot;}

Para obtener información sobre cómo se informan los visitantes únicos, consulte [Visitantes únicos en Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=es).
