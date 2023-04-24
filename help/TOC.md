---
cloud: platform-cloud
audience: end-user
user-guide-title: Asistencia del servicio de identidad de Experience Cloud
breadcrumb-title: Guía del servicio de identidad
user-guide-description: El servicio Adobe Experience Cloud ID ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. Ayuda a reemplazar el código de generación de ID heredado en soluciones y servicios de Experience Cloud.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 98%

---


# Asistencia del servicio de identidad de Experience Cloud {#using}

+ [Ayuda del servicio de identidad](home.md)
+ Información general {#intro}
   + [Información general](introduction/overview.md)
   + [Acerca del servicio de ID](introduction/about-id-service.md)
   + [Cookies y el servicio de ID](introduction/cookies.md)
   + [Solicitud y configuración de ID con el servicio de ID](introduction/id-request.md)
   + [Conceptos básicos de sincronización y tasas de coincidencia](introduction/match-rates.md)
+ Implementación {#implementation}
   + [Métodos de implementación](implementation-guides/implementation-methods.md)
   + [Guías de implementación](implementation-guides/implementation-guides.md)
   + [Implementación con etiquetas de Experience Platform](implementation-guides/ecid-implement-with-launch.md)
   + [Implementar para Analytics](implementation-guides/setup-analytics.md)
   + [Implementar para Target](implementation-guides/setup-target.md)
   + [Implementar para Analytics y Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementar para Analytics, Audience Manager y Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servicio ID con A4T y una implementación de Target en el lado del servidor](implementation-guides/ecid-a4t-target.md)
   + [Integración directa con el servicio ID](implementation-guides/direct-integration.md)
   + [Casos de uso de integraciones directas](implementation-guides/direct-integration-examples.md)
   + [Comprobación y verificación del servicio ID](implementation-guides/test-verify.md)
   + Servicio de inclusión {#opt-in-service}
      + [Información general sobre el servicio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuración del servicio de inclusión](implementation-guides/opt-in-service/getting-started.md)
      + [Validación del servicio de inclusión](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuración de inclusión con Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuración de inclusión con DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Actividades de control de Experience Cloud basadas en el consentimiento del usuario](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Casos de uso de inclusión](implementation-guides/opt-in-service/use-cases.md)
      + [Referencia de inclusión](implementation-guides/opt-in-service/api.md)
      + [Uso de servicios de inclusión con IAB Framework](implementation-guides/opt-in-service/iab.md)
+ API del servicio de ID {#id-service-api}
   + [Información general de API del servicio de ID](library/library.md)
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
   + Referencia de Analytics {#analytics-reference}
      + [Información general de referencia de Analytics](reference/analytics-reference/analytics-reference.md)
      + [Información general sobre la implementación de CNAME](reference/analytics-reference/cname.md)
      + [Configuración de Analytics y Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Orden de operaciones para los ID de Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Puntos de decisión para la migración del servicio de ID](reference/analytics-reference/migration-decisions.md)
      + [Escenarios de migración del servicio de ID](reference/analytics-reference/migration-scenarios.md)
      + [Solicitudes de Analytics e identidad](reference/analytics-reference/legacy-analytics.md)
      + [Implementación del lado del servidor combinada con JavaScript](reference/analytics-reference/server-side.md)
      + [Período de gracia del servicio de ID](reference/analytics-reference/grace-period.md)
   + [Cambios en el etiquetado de SameSite de Google Chrome](reference/chrome-samesite-labelling.md)
   + [Políticas de seguridad del contenido y el servicio ID](reference/csp.md)
   + [Compatibilidad con COPPA en el servicio ID](reference/coppa.md)
   + [Compatibilidad con CORS en el servicio ID](reference/cors.md)
   + [ID de cliente y estados de autenticación](reference/authenticated-state.md)
   + [Métodos de biblioteca ECID en un entorno de Safari ITP](reference/ecid-library-methods.md)
   + [Identificación de visitantes únicos](reference/unique-vis-method.md)
   + [Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID](reference/regions.md)
   + [Requisitos del servicio ID](reference/requirements.md)
   + [Monitoreo de vídeo y servicio ID](reference/heartbeat.md)
   + [Data Workbench y el servicio ID](reference/dwb.md)
   + [Soporte hash SHA256 para setCustomerIDs](reference/hashing-support.md)
+ Preguntas más frecuentes {#faqs}
   + [Información general sobre preguntas más frecuentes](faq-intro/faq-intro.md)
   + [Preguntas más frecuentes sobre el servicio de ID](faq-intro/faq.md)
   + [Preguntas más frecuentes sobre el servicio de ID y Analytics](faq-intro/analytics-faq.md)
   + [Preguntas frecuentes para otras soluciones de Experience Cloud](faq-intro/other-faq.md)
+ Notas de la versión del servicio de ID {#release-notes}
   + [Notas de la versión 2022](release-notes/notes-2022.md)
   + [Notas de la versión 2021](release-notes/notes-2021.md)
   + [Notas de la versión de 2020](release-notes/notes-2020.md)
   + [Notas de la versión de 2019](release-notes/notes-2019.md)
   + [Notas de la versión de 2018](release-notes/notes-2018.md)
   + [Notas de la versión 2017](release-notes/notes-2017.md)
   + [Notas de la versión 2016](release-notes/notes-2016.md)
   + [Notas de la versión 2015](release-notes/notes-2015.md)
+ [Prueba de Analytics oculta en TOC](analytics-test-file-hidetoc.md)
