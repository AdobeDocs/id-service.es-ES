---
description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento de inclusión de Audience Manager para el marco de transparencia y consentimiento de IAB (TCF).
seo-description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento de Audience Manager para el marco de transparencia y consentimiento de IAB (TCF).
seo-title: Uso de servicios de inclusión con IAB Framework
title: Uso de servicios de inclusión con IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 66%

---


# Uso de servicios de inclusión con IAB Framework {#using-opt-in-services-with-iab-framework}

Conecte la plataforma de administración de consentimiento (CMP) con el complemento Audience Manager de inclusión para TCF de IAB.

Los clientes de Audience Manager que utilizan el [marco de transparencia y consentimiento (TCF) de IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) pueden conectar su plataforma de administración de consentimiento (CMP) con el complemento de inclusión de Audience Manager para el TCF de IAB. El servicio de inclusión (Opt-in) es una función integrada en la biblioteca JavaScript de ECID que puede deshabilitar bibliotecas determinadas de soluciones de Adobe, en función de las preferencias del visitante, que se establecen dentro de una plataforma CMP. Cuando el complemento Administrador de Audiencias para TCF IAB se implementa con la biblioteca ECID, las preferencias de visitante de su CMP que admite TCF IAB se asignan automáticamente a la opción de inclusión. Estas preferencias activarán bibliotecas basadas en Audience Manager (DIL y ECID) y llamadas asociadas cuando se reciba el consentimiento.

## Implementar una CMP compatible con IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para que la opción de inclusión se integre con el TCF de IAB, debe completar lo siguiente:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Defina/Cargue `__cmp` antes de cargar Adobe JS.

Para obtener más información, consulte los [documentos del Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Habilite el complemento de Audience Manager para TCF de IAB en la biblioteca JavaScript de ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>La inclusión solo está disponible en ECID 4.0+.

Utilice Adobe Experience Platform Launch para implementar tanto el complemento de inclusión como el Audience Manager para IAB en su sitio. Al habilitar IAB para la opción de inclusión de forma manual, asegúrese de que la siguiente configuración se establece en true en el objeto Visitante:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Una vez que la configuración sea correcta, las bibliotecas ECID y DIL se habilitarán o deshabilitarán según los criterios de consentimiento de CMP y IAB TCF.

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. [Acceda](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html) a la documentación de Audience Manager para obtener más información sobre el complemento Audience Manager para TCF de IAB.

Para obtener más información sobre cómo se validan los complementos de inclusión y de Audience Manager para TCF de IAB, consulte el caso n.º 4 de la guía de validación [aquí](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentación relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Marco de transparencia y consentimiento (TCF) de IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): para obtener más información sobre el IAB estándar
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): para obtener más información acerca de Opt-In, un componente necesario para la gestión del consentimiento en las soluciones de plataforma
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.translate.html)
* [Sus decisiones de privacidad](https://www.adobe.com/es/privacy/opt-out.html#customeruse): otra opción de privacidad a disposición de los usuarios es la capacidad de excluirse de toda recopilación de datos mediante otras herramientas globales de exclusión. La exclusión global tiene prioridad sobre la verificación TCF de inclusión e IAB

