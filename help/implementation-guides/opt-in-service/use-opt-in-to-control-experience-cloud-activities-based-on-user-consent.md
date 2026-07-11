---
title: Utilice la inclusión para controlar las actividades empresariales de CX en función del consentimiento del usuario
description: El objeto de inclusión de Adobe es una extensión del servicio de ID de visitante de Adobe, diseñado para ayudarle a controlar si las soluciones de CX Enterprise pueden crear cookies en páginas web o iniciar señalizaciones, según el consentimiento del usuario final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 28%

---

# Actividades empresariales de CX de control basadas en el consentimiento del usuario

El objeto de Adobe [!UICONTROL Opt-in] es una extensión del servicio de ID de visitante de Adobe, diseñado para ayudarle a controlar si las soluciones de CX Enterprise pueden crear cookies en páginas web o iniciar señalizaciones, según el consentimiento del usuario final.

## Conceptos básicos de [!UICONTROL Opt-In]

Un aspecto importante de las normas de privacidad es la adquisición y transmisión del consentimiento del usuario sobre cómo se pueden utilizar sus datos personales y quién los puede usar. La última versión del servicio de ID de visitante incluye la funcionalidad que proporciona activación condicional (como consentimiento previo y posterior) de las etiquetas de la solución CX Enterprise, en función de si se da el consentimiento del usuario final. Este proceso se muestra en la siguiente imagen:

![Diagrama del funcionamiento de [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] funciona de la siguiente manera:

**Si [!UICONTROL Opt-in] está habilitado en el servicio de ID de visitante (a través de una variable booleana), retrasa las bibliotecas de la solución CX Enterprise de activar etiquetas o configurar cookies hasta que se haya dado el consentimiento para esa solución.**

[!UICONTROL Opt-in] también le permite decidir si se activa alguna etiqueta antes del consentimiento del usuario y, a continuación, se almacena esta información de consentimiento (con el consentimiento del usuario final) para que pueda utilizarse en visitas posteriores. El almacenamiento del consentimiento está disponible en las opciones [!UICONTROL Opt-in], o bien se puede integrar con una CMP y almacenar las selecciones de consentimiento.

## Habilitando y configurando [!UICONTROL Opt-In]

[!UICONTROL Opt-in] se puede configurar más fácilmente con etiquetas. Vea el siguiente vídeo breve para ver cómo.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si no usa etiquetas, puede establecer la configuración de [!UICONTROL Opt-in] en la inicialización del objeto de Visitante global, como se muestra en la [documentación](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=es).

## Implementando [!UICONTROL Opt-In] en la página

Todo este proceso de configuración y back-end está preparado para proporcionar una interfaz para que los visitantes del sitio se presenten con opciones de consentimiento. Usted mismo puede crear esta interfaz de usuario o puede usar un socio de CMP (Plataforma de administración de consentimiento) para crear la interfaz de usuario.

Al configurar una interfaz de usuario para usar [!UICONTROL Opt-in] con el fin de obtener el consentimiento, debe configurarse para llamar a las API que se conectarán a [!UICONTROL Opt-in] e informarlas para dar su consentimiento a algunas o todas las soluciones de Adobe CX Enterprise. Encontrará información detallada sobre estas API en la [documentación de referencia de inclusión](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=es). También encontrará información adicional sobre la inclusión en las páginas de documentación que la rodean.

## Demostración de [!UICONTROL Opt-In]

En el siguiente vídeo, vea una demostración rápida de [!UICONTROL Opt-in] trabajando en la página y cómo puede afectar si las soluciones de CX Enterprise pueden configurar cookies, iniciar señalizaciones, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** Es importante tener en cuenta que en el momento de escribir este artículo, [!UICONTROL Opt-in] no se ha integrado en las bibliotecas para todas las aplicaciones de CX Enterprise. Las bibliotecas admitidas actualmente para [!UICONTROL Opt-in] son:

* Servicio de ID de visitante
* Analytics
* Audience Manager
* Target

