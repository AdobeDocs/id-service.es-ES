---
title: Identificación de visitantes únicos
description: Documentación de Adobe ECID (servicio de ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
TQID: https://experienceleague.adobe.com/1iZMkBA6-SnhhVmqp8qrFuk-Ev-tKOae5FAduivghXM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 251
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

{style="table-layout:auto"}

Para obtener información sobre cómo se informan los visitantes únicos, consulte [Visitantes únicos en Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=es).

