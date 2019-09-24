---
description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de inclusión.
seo-description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de inclusión.
seo-title: (beta) Uso de servicios de inclusión con IAB Framework
title: (beta) Uso de servicios de inclusión con IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# (beta) Uso de servicios de inclusión con IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de inclusión.

Audience Manager customers using [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) can connect their Consent Management Platform (CMP) with Opt-in’s IAB plugin. El servicio de inclusión (Opt-in) es una función integrada en la biblioteca JavaScript de ECID que puede deshabilitar bibliotecas determinadas de soluciones de Adobe, en función de las preferencias del visitante, que se establecen dentro de una plataforma CMP. Cuando se implementa el complemento IAB con la biblioteca ECID, las preferencias de visitante de su CMP compatible con IAB se asignan automáticamente al servicio de inclusión (Opt-in). Estas preferencias activarán bibliotecas basadas en Audience Manager (DIL y ECID) y llamadas asociadas cuando se reciba el consentimiento.

## Implementar una CMP compatible con IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para que Opt-In se integre con el consentimiento IAB necesita completar las siguientes acciones:

1. Implemente una CMP que sea compatible con IAB y esté [registrada como proveedor IAB](https://vendorlist.consensu.org/vendorlist.json), o desarrolle una CMP interna que implemente la especificación IAB y, a continuación, regístrela como CMP en IAB Europe.
1. Defina/Cargue `__cmp` antes de cargar Adobe JS.

Para obtener más información, consulte los [documentos del Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Habilitar el complemento IAB dentro de su biblioteca JavaScript de ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>El servicio de inclusión (Opt-in) solo está disponible en la versión de ECID 4.0 y posteriores

Utilice Adobe Experience Plaform Launch para implementar tanto Opt-in como el complemento IAB para su sitio. Read the [documentation for the ECID Opt-in extension](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) to learn how to set up the Experience Platform Launch extension.

Cuando habilite IAB para Opt-in de forma manual, asegúrese de que los siguientes ajustes estén establecidos en “true” dentro del objeto Visitor:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Una vez que los ajustes estén correctamente configurados, las bibliotecas ECID y DIL se habilitan o deshabilitan, en función de los criterios de consentimiento de la CMP y el marco IAB.

>[!IMPORTANT]
>
>Audience Manager necesita consentimiento para las *finalidades 1, 2 y 5, además del consentimiento del proveedor*, para poder implementar cookies e iniciar o cumplir sincronizaciones de ID. Obtenga más información sobre el complemento IAB en la documentación de Audience Manager [aquí](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).

Para obtener más información sobre cómo se validan tanto Opt-in como el complemento IAB, consulte el caso n.º 4 de la guía de validación [aquí](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentación relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Marco de transparencia y consentimiento (TCF) de IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): para obtener más información sobre el IAB estándar
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): para obtener más información acerca de Opt-In, un componente necesario para la gestión del consentimiento en las soluciones de plataforma
* Soporte para el marco de transparencia y consentimiento (TCF) de IAB [en Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Sus decisiones de privacidad](https://www.adobe.com/privacy/opt-out.html#customeruse): otra opción de privacidad a disposición de los usuarios es la capacidad de excluirse de toda recopilación de datos mediante otras herramientas globales de exclusión. La Exclusión global tiene preferencia sobre la verificación mediante Opt-in e IAB

