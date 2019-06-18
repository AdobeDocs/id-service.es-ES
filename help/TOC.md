---
cloud: experience-cloud
product: Servicio de ID
audience: usuario final
user-guide-title: Ayuda del servicio de ID
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Ayuda del servicio de ID {#using}

+ [Servicio Experience Cloud ID](mcvid-home.md)
+ Información general  {#mcvid-introduction}
   + [Información general  ](mcvid-introduction/mcvid-overview.md)
   + [Acerca del servicio de ID](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookies y el servicio Experience Cloud ID](mcvid-introduction/mcvid-cookies.md)
   + [Cómo solicita y establece los ID el servicio Experience Cloud ID](mcvid-introduction/mcvid-id-request.md)
   + [Conceptos básicos de sincronización de ID y tasas de coincidencia](mcvid-introduction/mcvid-match-rates.md)
+ Guías de implementación {#implementation-guides}
   + [Guías de implementación](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [Métodos de implementación](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Implementación con Launch](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [Implementación con la administración dinámica de etiquetas](mcvid-implementation-guides/mcvid-standard.md)
   + [Implementación del servicio Experience Cloud ID para Analytics](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Implementación del servicio Experience Cloud ID para Target](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Implementación del servicio Experience Cloud ID para Analytics y Audience Manager](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Implementación del servicio Experience Cloud ID para Analytics, Audience Manager y Target](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Uso del servicio Experience Cloud ID con A4T y una implementación de Target en el lado del servidor](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Integración directa con el servicio Experience Cloud ID](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [Casos de uso de integración directa](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [Probar y verificar el servicio Experience Cloud ID](mcvid-implementation-guides/mcvid-test-verify.md)
   + Documentación de inclusión {#opt-in-service}
      + [Información general sobre el servicio de inclusión](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [Configuración del servicio de selección](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [Validación del servicio de selección](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuración de Opt-in con Launch](mcvid-implementation-guides/opt-in-service/launch.md)
      + [Configuración de Opt-in con DTM](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [Casos de uso de Opt-in](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [Referencia de Opt-in](mcvid-implementation-guides/opt-in-service/api.md)
      + [(beta) Uso de servicios de inclusión con IAB Framework](mcvid-implementation-guides/opt-in-service/iab.md)
+ API del servicio de ID {#id-service-api}
   + [Información general de API de servicio de ID](mcvid-library/mcvid-library.md)
   + Configuración {#configurations}
      + [Información general sobre configuraciones](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer y audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain y whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + Métodos {#methods}
      + [Métodos](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (seguimiento entre dominios)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [Métodos callTimeOut](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [Sincronización de ID por dirección URL o fuente de datos](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ Referencia {#reference}
   + [Información general de referencia](mcvid-reference/mcvid-reference.md)
   + Referencia de Analytics {#analytics-reference}
      + [Información general de referencia de Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Configuración de Analytics y Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Orden de operaciones para los ID de Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Puntos de decisión para la migración del servicio Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Escenarios de migración del servicio Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Solicitudes de ID de Analytics y Experience Cloud](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [CNAME de recopilación de datos y seguimiento entre dominios](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [Implementación del lado del servidor combinada con JavaScript](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [Período de gracia del servicio de ID](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)
   + [Políticas de seguridad del contenido y el servicio Experience Cloud ID](mcvid-reference/mcvid-csp.md)
   + [Compatibilidad con COPPA en el servicio Experience Cloud ID](mcvid-reference/mcvid-coppa.md)
   + [Compatibilidad con CORS en el servicio Experience Cloud ID](mcvid-reference/mcvid-cors.md)
   + [ID de cliente y estados de autenticación](mcvid-reference/mcvid-authenticated-state.md)
   + [Métodos de biblioteca ECID en un mundo Safari ITP](mcvid-reference/ecid-library-methods.md)
   + [Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID](mcvid-reference/mcvid-regions.md)
   + [Requisitos del servicio Experience Cloud ID](mcvid-reference/mcvid-requirements.md)
   + [Monitoreo de vídeo y servicio Experience Cloud ID](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench y el servicio Experience Cloud ID](mcvid-reference/mcvid-dwb.md)
+ Preguntas más frecuentes {#faqs}
   + [Información general sobre preguntas más frecuentes](mcvid-faq-intro/mcvid-faq-intro.md)
   + [Preguntas más frecuentes sobre el servicio de ID](mcvid-faq-intro/mcvid-faq.md)
   + [Preguntas más frecuentes sobre el servicio de ID y Analytics](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [Preguntas más frecuentes para otras soluciones de Experience Cloud](mcvid-faq-intro/mcvid-other-faq.md)
+ Notas de la versión del servicio de ID {#release-notes}
   + [Notas de la versión 2019](mcvid-release-notes/mcvid-release-notes.md)
   + [Notas de la versión 2018](mcvid-release-notes/mcvid-notes-2018.md)
   + [Notas de la versión 2017](mcvid-release-notes/mcvid-notes-2017.md)
   + [Notas de la versión 2016](mcvid-release-notes/mcvid-notes-2016.md)
   + [Notas de la versión 2015](mcvid-release-notes/mcvid-notes-2015.md)
