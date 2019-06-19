---
cloud: platform-cloud
product: Servicio de identidad
audience: usuario final
user-guide-title: Ayuda del servicio de identidad de la plataforma de experiencia
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 1af38efa5e85c09548a6dee6c9c550900f90a8ed

---


# Ayuda del servicio de identidad {#using}

+ [Ayuda del servicio de identidad](home.md)
+ Información general  {#intro}
   + [Información general  ](introduction/overview.md)
   + [Acerca del servicio de identidad](introduction/about-id-service.md)
   + [Cookies y el servicio de identidad](introduction/cookies.md)
   + [Cómo solicita y establece los ID el servicio de identidad](introduction/id-request.md)
   + [Conceptos básicos de sincronización y tasas de coincidencia](introduction/match-rates.md)
+ Guías de implementación {#implementation-guides}
   + [Guías de implementación](implementation-guides/implementation-guides.md)
   + [Métodos de implementación](implementation-guides/implementation-methods.md)
   + [Implementación con Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Implementación con DTM](implementation-guides/standard.md)
   + [Implementar para Analytics](implementation-guides/setup-analytics.md)
   + [Implementar para Target](implementation-guides/setup-target.md)
   + [Implementación para Analytics y Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementar para Analytics, Audience Manager y Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servicio de identidad con A 4 T y una implementación de servidor de Target](implementation-guides/ecid-a4t-target.md)
   + [Integración directa con el servicio de identidad](implementation-guides/direct-integration.md)
   + [Casos de uso de integración directa](implementation-guides/direct-integration-examples.md)
   + [Comprobación y verificación del servicio de identidad](implementation-guides/test-verify.md)
   + Documentación de inclusión {#opt-in-service}
      + [Información general sobre el servicio de inclusión](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuración del servicio de selección](implementation-guides/opt-in-service/getting-started.md)
      + [Validación del servicio de selección](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuración de Opt-in con Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuración de Opt-in con DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Casos de uso de Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Referencia de Opt-in](implementation-guides/opt-in-service/api.md)
      + [(beta) Uso de servicios de inclusión con IAB Framework](implementation-guides/opt-in-service/iab.md)
+ API de servicio de identidad {#id-service-api}
   + [Información general de la API de servicio de identidad](library/library.md)
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
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
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
   + Referencia de Analytics {#analytics-reference}
      + [Información general de referencia de Analytics](reference/analytics-reference/analytics-reference.md)
      + [Configuración de Analytics e identificadores](reference/analytics-reference/analytics-ids.md)
      + [Orden de operaciones para los ID de Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Puntos de decisión para la migración del servicio de identidad](reference/analytics-reference/migration-decisions.md)
      + [Escenarios de migración de servicios de identidad](reference/analytics-reference/migration-scenarios.md)
      + [Análisis y solicitudes de identidad](reference/analytics-reference/legacy-analytics.md)
      + [CNAME de recopilación de datos y seguimiento entre dominios](reference/analytics-reference/cname.md)
      + [Implementación del lado del servidor combinada con JavaScript](reference/analytics-reference/server-side.md)
      + [Período de gracia del servicio de identidad](reference/analytics-reference/grace-period.md)
   + [Políticas de seguridad de contenido y el servicio de identidad](reference/csp.md)
   + [Compatibilidad con COPPA en el servicio de identidad](reference/coppa.md)
   + [Compatibilidad con CORS en el servicio de identidad](reference/cors.md)
   + [ID de cliente y estados de autenticación](reference/authenticated-state.md)
   + [Métodos de biblioteca ECID en un mundo Safari ITP](reference/ecid-library-methods.md)
   + [Obtención de ID de región y de usuario desde la cookie AMCV o el servicio de identidad](reference/regions.md)
   + [Requisitos del servicio de identidad](reference/requirements.md)
   + [Video Heartbeat y el servicio de identidad](reference/heartbeat.md)
   + [Área de trabajo de datos y servicio de identidad](reference/dwb.md)
+ Preguntas más frecuentes {#faqs}
   + [Información general sobre preguntas más frecuentes](faq-intro/faq-intro.md)
   + [Preguntas frecuentes sobre el servicio de identidad](faq-intro/faq.md)
   + [Preguntas frecuentes sobre el servicio de identidad y Analytics](faq-intro/analytics-faq.md)
   + [Preguntas más frecuentes para otras soluciones de Experience Cloud](faq-intro/other-faq.md)
+ Notas de la versión del servicio de identidad {#release-notes}
   + [Notas de la versión 2019](release-notes/release-notes.md)
   + [Notas de la versión 2018](release-notes/notes-2018.md)
   + [Notas de la versión 2017](release-notes/notes-2017.md)
   + [Notas de la versión 2016](release-notes/notes-2016.md)
   + [Notas de la versión 2015](release-notes/notes-2015.md)
