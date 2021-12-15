---
title: Use la opción de inclusión para controlar Actividades de Experience Cloud basadas en el consentimiento del usuario
description: El objeto de inclusión de Adobe es una extensión del servicio de identidad de Adobe Experience Platform, diseñado para ayudarle a controlar si las soluciones de Experience Cloud pueden crear cookies en páginas web o iniciar señalizaciones, según el consentimiento del usuario final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# Actividades de control de Experience Cloud basadas en el consentimiento del usuario

El Adobe [!UICONTROL Inclusión] El objeto es una extensión del Adobe [!UICONTROL Servicio de identidad de Experience Platform], diseñado para ayudarle a controlar si las soluciones de Experience Cloud pueden crear cookies en páginas web o iniciar señalizaciones, según el consentimiento del usuario final, y cuáles pueden hacerlo.

## Aspectos básicos de la [!UICONTROL inclusión]

Un aspecto importante de las normas de privacidad es la adquisición y transmisión del consentimiento del usuario sobre cómo se pueden utilizar sus datos personales y quién los puede usar. La última versión de [!UICONTROL Servicio de identidad] incluye funcionalidad que proporciona activación condicional (como consentimiento previo y posterior) de las etiquetas de la solución Experience Cloud, en función de si se da el consentimiento del usuario final. Este proceso se muestra en la siguiente imagen:

![ Diagrama del funcionamiento de la [!UICONTROL  inclusión] ](assets/opt-in.png)

[!UICONTROL Inclusión] funciona de la siguiente manera:

**Si la opción de [!UICONTROL inclusión] está habilitada en el servicio de identidad (a través de una variable booleana), retrasa las bibliotecas de la solución Experience Cloud de activar etiquetas o configurar cookies hasta que se haya dado el consentimiento para esa solución.**

[!UICONTROL Inclusión] también le permite decidir si las etiquetas se activan antes del consentimiento del usuario y, a continuación, esta información de consentimiento (junto con el consentimiento dado por el usuario final) se almacena para que se pueda utilizar en visitas posteriores. El almacenamiento del consentimiento está disponible en las opciones de [!UICONTROL inclusión] o se puede integrar con un CMP y almacenar las selecciones de consentimiento.

## Activación y configuración de la [!UICONTROL inclusión]

[!UICONTROL Inclusión] es más fácil de configurar con etiquetas de Adobe Experience Platform (anteriormente, Launch). Vea el siguiente vídeo para ver cómo.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si no utiliza etiquetas de Experience Platform, puede establecer [!UICONTROL Inclusión]La configuración de en la inicialización del objeto de visitante global, como se muestra en la variable [documentación](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementación de la [!UICONTROL inclusión] en la página

Todo este proceso de configuración y back-end está preparado para proporcionar una interfaz para que los visitantes del sitio se presenten con opciones de consentimiento. Usted mismo puede crear esta interfaz de usuario o puede usar un socio de CMP (Plataforma de administración de consentimiento) para crear la interfaz de usuario.

Al configurar una interfaz de usuario para utilizar la opción de [!UICONTROL inclusión] para obtener el consentimiento, debe configurarse para llamar a las API que se conectarán con la opción de [!UICONTROL inclusión] e informarlas para dar su consentimiento a algunas o todas las soluciones de Adobe Experience Cloud. Encontrará información detallada sobre estas API en la [documentación de referencia de inclusión](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). También encontrará información adicional sobre la inclusión en las páginas de documentación que la rodean.

## Demostración de [!UICONTROL inclusión]

En el siguiente vídeo, vea una demostración rápida de [!UICONTROL Inclusión] trabajar en la página y cómo puede afectar si las soluciones de Experience Cloud pueden configurar cookies, iniciar señalizaciones, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** Es importante señalar que en el momento de redactar este artículo, [!UICONTROL Inclusión] no se ha integrado en las bibliotecas de para todas las aplicaciones de Experience Cloud. Las bibliotecas admitidas actualmente para la [!UICONTROL inclusión] son:

* Servicio de identidad
* Analytics
* Audience Manager
* [!DNL Target]
