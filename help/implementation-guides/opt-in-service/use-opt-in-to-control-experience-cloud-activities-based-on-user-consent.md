---
title: Use la opción de inclusión para controlar Actividades de Experience Cloud basadas en el consentimiento del usuario
description: El objeto de selección de Adobe es una extensión del servicio de identidad de Adobe Experience Platform, diseñado para ayudarle a controlar si las soluciones de Experience Cloud pueden crear cookies en páginas web o iniciar señalizaciones en función del consentimiento del usuario final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '554'
ht-degree: 100%

---

# Actividades de control de Experience Cloud basadas en el consentimiento del usuario

El [!UICONTROL objeto de inclusión] de Adobe es una extensión del [!UICONTROL servicio de identidad de Experience Platform] de Adobe, diseñado para ayudarle a controlar si las soluciones de Experience Cloud pueden crear cookies en páginas web o iniciar señalizaciones, según el consentimiento del usuario final.

## Aspectos básicos de la [!UICONTROL inclusión]

Un aspecto importante de las normas de privacidad es la adquisición y transmisión del consentimiento del usuario sobre cómo se pueden utilizar sus datos personales y quién los puede usar. La última versión de [!UICONTROL Identity Service] incluye funcionalidad, que se encuentra entre el usuario (la interfaz de usuario) y las soluciones de Adobe y proporciona activación condicional (por ejemplo, consentimiento previo y posterior) de las etiquetas de la solución de Adobe Experience Cloud en función de si el usuario final ha dado su consentimiento. Esto se muestra en la siguiente imagen:

![ Diagrama del funcionamiento de la [!UICONTROL  inclusión] ](assets/opt-in.png)

[!UICONTROL La inclusión] es básicamente el portero... ¿O es el amo de llaves? Tú decides.

Esto se reduce a esto:

**Si la opción de [!UICONTROL inclusión] está habilitada en el servicio de identidad (a través de una variable booleana), retrasa las bibliotecas de la solución Experience Cloud de activar etiquetas o configurar cookies hasta que se haya dado el consentimiento para esa solución.**

[!UICONTROL La inclusión] también le permite decidir si se activa alguna etiqueta *antes* del consentimiento del usuario y, a continuación, se almacena esta información de consentimiento (con el consentimiento del usuario final) para que pueda utilizarse en visitas posteriores. El almacenamiento del consentimiento está disponible en las opciones de [!UICONTROL inclusión] o se puede integrar con un CMP y almacenar las selecciones de consentimiento.

## Activación y configuración de la [!UICONTROL inclusión]

[!UICONTROL La inclusión] también es más fácil de configurar con Adobe Experience Platform Launch. Vea el siguiente vídeo para ver cómo.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si no utiliza Experience Platform Launch, puede definir la configuración de [!UICONTROL inclusión] en la inicialización del objeto de Visitante global, como se muestra en la [documentación](https://marketing.adobe.com/resources/help/es_ES/mcvid/getting-started.html).

## Implementación de la [!UICONTROL inclusión] en la página

Todo este proceso de configuración y back-end está preparado para proporcionar una interfaz para que los visitantes del sitio se presenten con opciones de consentimiento. Usted mismo puede crear esta interfaz de usuario o puede usar un socio de CMP (Plataforma de administración de consentimiento) para crear la interfaz de usuario.

Al configurar una interfaz de usuario para utilizar la opción de [!UICONTROL inclusión] para obtener el consentimiento, debe configurarse para llamar a las API que se conectarán con la opción de [!UICONTROL inclusión] e informarlas para dar su consentimiento a algunas o todas las soluciones de Adobe Experience Cloud. Encontrará información detallada sobre estas API en la [documentación de referencia de inclusión](https://marketing.adobe.com/resources/help/es_ES/mcvid/api.html). También encontrará información adicional sobre la inclusión en las páginas de documentación que la rodean.

## Demostración de [!UICONTROL inclusión]

En el siguiente vídeo, vea una demostración rápida de la [!UICONTROL inclusión] en la página y cómo puede afectar si las soluciones Experience Cloud pueden configurar cookies, iniciar señalizaciones, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** Es importante señalar que, en el momento de escribir este artículo, la [!UICONTROL inclusión] no se ha incorporado en las bibliotecas de todas las soluciones de Experience Cloud. Las bibliotecas admitidas actualmente para la [!UICONTROL inclusión] son:

* Servicio de identidad
* Analytics
* Audience Manager
* [!DNL Target]
