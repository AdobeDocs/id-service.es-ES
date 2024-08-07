---
description: Métodos de implementación estándar y no estándar del servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Métodos de implementación
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '129'
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
