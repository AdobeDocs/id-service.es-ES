---
audience: end-user
user-guide-title: Ayuda del servicio de ID de visitante de Adobe
breadcrumb-title: Guía del servicio de ID de visitante
user-guide-description: El servicio de ID de visitante de Adobe ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de CX Enterprise. Ayuda a reemplazar el código de generación de ID heredado para las soluciones y servicios de CX Enterprise.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 46%

---


# Ayuda del servicio de ID de visitante de Adobe {#using}

+ [Ayuda del servicio de ID de visitante](home.md)
+ Información general {#intro}
   + [Información general](introduction/overview.md)
   + [Acerca del servicio de ID de visitante](introduction/about-id-service.md)
   + [Cookies y el servicio de ID de visitante](introduction/cookies.md)
   + [Solicitud y configuración de ID con el servicio de ID de visitante](introduction/id-request.md)
   + [Conceptos básicos de sincronización y tasas de coincidencia](introduction/match-rates.md)
+ Implementación {#implementation}
   + [Métodos de implementación](implementation-guides/implementation-methods.md)
   + [Guías de implementación](implementation-guides/implementation-guides.md)
   + [Implementación con etiquetas](implementation-guides/ecid-implement-with-launch.md)
   + [Implementar para Analytics](https://experienceleague.adobe.com/es/docs/analytics/implementation/id/overview){target=_blank}
   + [Implementar para Target](implementation-guides/setup-target.md)
   + [Implementar para Analytics y Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementar para Analytics, Audience Manager y Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servicio de ID de visitante con A4T y una implementación de Target en el lado del servidor](implementation-guides/ecid-a4t-target.md)
   + [Integración directa con el servicio de ID de visitante](implementation-guides/direct-integration.md)
   + [Casos de uso de integraciones directas](implementation-guides/direct-integration-examples.md)
   + [Comprobación y verificación del servicio de ID de visitante](implementation-guides/test-verify.md)
   + servicio de inclusión (Opt-in) {#opt-in-service}
      + [Información general sobre el servicio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuración del servicio de inclusión](implementation-guides/opt-in-service/getting-started.md)
      + [Validación del servicio de inclusión](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuración de Opt-in con etiquetas](implementation-guides/opt-in-service/launch.md)
      + [Actividades empresariales de CX de control basadas en el consentimiento del usuario](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Casos de uso de inclusión](implementation-guides/opt-in-service/use-cases.md)
      + [Referencia de inclusión](implementation-guides/opt-in-service/api.md)
      + [Uso de servicios de inclusión con IAB Framework](implementation-guides/opt-in-service/iab.md)
+ API del servicio de ID de visitante {#id-service-api}
   + [Resumen de API del servicio de ID de visitante](library/library.md)
   + Configuración {#configurations}
      + [Información general sobre configuraciones](library/function-vars/function-vars.md)
      + [audienceManagerServer y audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Configuraciones seguras y SameSite](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain y whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Métodos {#methods}
      + [Métodos](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (seguimiento entre dominios)](library/get-set/appendvisitorid.md)
      + [Métodos callTimeOut](library/get-set/timeout-functions.md)
      + [Sincronización de ID por dirección URL o fuente de datos](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Referencia {#reference}
   + [Información general de referencia](reference/reference.md)
   + [Cambios en el etiquetado de SameSite de Google Chrome](reference/chrome-samesite-labelling.md)
   + [Políticas de seguridad del contenido y el servicio de ID de visitante](reference/csp.md)
   + [Compatibilidad con COPPA en el servicio de ID de visitante](reference/coppa.md)
   + [Compatibilidad con CORS en el servicio de ID de visitante](reference/cors.md)
   + [ID de cliente y estados de autenticación](reference/authenticated-state.md)
   + [Métodos de biblioteca ECID en un entorno de Safari ITP](reference/ecid-library-methods.md)
   + [Identificación de visitantes únicos](reference/unique-vis-method.md)
   + [Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID de visitante](reference/regions.md)
   + [Requisitos del servicio de ID de visitante](reference/requirements.md)
   + [Video Heartbeat y el servicio de ID de visitante](reference/heartbeat.md)
   + [Soporte hash SHA256 para setCustomerIDs](reference/hashing-support.md)
+ Preguntas frecuentes {#faqs}
   + [Información general sobre preguntas más frecuentes](faq-intro/faq-intro.md)
   + [Preguntas frecuentes sobre el servicio de ID de visitante](faq-intro/faq.md)
   + [Preguntas frecuentes para otras soluciones de CX para empresas](faq-intro/other-faq.md)
+ Notas de la versión del servicio de ID de visitante {#release-notes}
   + [Notas de la versión de 2022](release-notes/notes-2022.md)
   + [Notas de la versión de 2021](release-notes/notes-2021.md)
   + [Notas de la versión de 2020](release-notes/notes-2020.md)
   + [Notas de la versión de 2019](release-notes/notes-2019.md)
   + [Notas de la versión de 2018](release-notes/notes-2018.md)
   + [Notas de la versión 2017](release-notes/notes-2017.md)
   + [Notas de la versión 2016](release-notes/notes-2016.md)
   + [Notas de la versión 2015](release-notes/notes-2015.md)
