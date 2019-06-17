---
description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de selección.
seo-description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de selección.
seo-title: (beta) Uso de servicios de inclusión con IAB Framework
title: (beta) Uso de servicios de inclusión con IAB Framework
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# (beta) Uso de servicios de inclusión con IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Conecte su plataforma de administración de consentimiento (CMP) con el complemento IAB de selección.

Los clientes de Audience Manager que utilizan [la IAB Transparencia y el Marco de consentimiento (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) pueden conectar su plataforma de administración de consentimiento (CMP) con el complemento IAB de selección. La inclusión es una función incrustada en la biblioteca ECID JavaScript que puede deshabilitar bibliotecas de soluciones de Adobe individuales según las preferencias del visitante establecidas en una CMP. Cuando el complemento IAB se implementa con la biblioteca ECID, las preferencias de los visitantes de la CMP compatible con IAB se asignan automáticamente a la opción de inclusión. Estas preferencias activarán bibliotecas basadas en Audience Manager (DIL y ECID) y llamadas asociadas cuando se reciba consentimiento.

## Implementar una CMP compatible con IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para que Opt-In se integre con el consentimiento IAB necesita completar las siguientes acciones:

1. Implemente una CMP que sea compatible con IAB y esté [registrada como proveedor IAB](https://vendorlist.consensu.org/vendorlist.json), o desarrolle una CMP interna que implemente la especificación IAB y, a continuación, regístrela como CMP en IAB Europe.
1. Defina o cargue antes `__cmp` de cargar el JS de Adobe.

Para obtener más información, consulte los [documentos del Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Habilitar el complemento IAB dentro de su biblioteca JavaScript de ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>La inclusión solo está disponible en ECID 4.0 +

Utilice Launch, de Adobe para implementar tanto Opt-in como el complemento IAB para su sitio. Lea la [documentación de la extensión ECID Opt-in](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) para aprender cómo se configura la extensión de Launch.

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
>Audience Manager necesita consentimiento para las *finalidades 1, 2 y 5, además del consentimiento del proveedor*, para poder implementar cookies e iniciar o cumplir sincronizaciones de ID. Obtenga más información sobre el complemento IAB en la documentación de Audience Manager** [aquí](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**.

Para obtener más información sobre cómo se validan tanto Opt-in como el complemento IAB, consulte el caso n.º 4 de la guía de validación [**aquí** ](../../mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentación relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Marco de transparencia y consentimiento (TCF) de IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): para obtener más información sobre el IAB estándar
* [Adobe Opt-In](../../mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): para obtener más información acerca de Opt-In, un componente necesario para la gestión del consentimiento en las soluciones de plataforma
* Soporte para el marco de transparencia y consentimiento (TCF) de IAB [en Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Sus decisiones de privacidad](https://www.adobe.com/privacy/opt-out.html#customeruse): otra opción de privacidad a disposición de los usuarios es la capacidad de excluirse de toda recopilación de datos mediante otras herramientas globales de exclusión. La Exclusión global tiene preferencia sobre la verificación mediante Opt-in e IAB

