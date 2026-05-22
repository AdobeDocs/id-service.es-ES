---
description: Métodos de implementación estándar y no estándar del servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Métodos de implementación
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 141
ht-degree: 100%

---

# Métodos de implementación

Puede elegir un [!DNL Experience Cloud ID Service] método de implementación estándar usando [!DNL Experience Platform Launch] o un método no estándar.

>[!IMPORTANT]
>
>Asegúrese de leer y comprender los [requisitos del servicio de ID](../reference/requirements.md) antes de comenzar con estos procedimientos.

## Implementación estándar {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe recomienda encarecidamente usar [[!DNL Experience Platform tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es) para implementar el servicio de ID. Este método garantiza la integración con otras soluciones de [!DNL Experience Cloud], optimiza los flujos de trabajo de implementación y garantiza automáticamente la colocación y secuenciación del código de manera correcta.

## Implementaciones no estándar {#section-2c4f2db1f9704315a7cccab6d2e07113}

Los procedimientos y ejemplos de código de esta guía pueden ayudarle a configurar el servicio de [!DNL Experience Cloud] ID de forma manual y sin seguir la configuración estándar. Tenga en cuenta que estas implementaciones suelen ser complejas y difíciles desde el punto de vista técnico. Es posible que necesite recursos de ingeniería, que son escasos, o que deba pedirle horas extra a su consultor del equipo de soporte de Adobe.

