---
description: El servicio de selección le permite configurar protocolos para que el visitante determine si puede configurar una cookie en el dispositivo o navegador del usuario al visitar el sitio.
seo-description: El servicio de selección le permite configurar protocolos para que el visitante determine si puede configurar una cookie en el dispositivo o navegador del usuario al visitar el sitio.
seo-title: Servicio de selección
title: Servicio de selección
uuid: aebd 72 ad -4118-471 b -9755-d 08 a 72 caa 0 fd
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Servicio de selección{#opt-in-service}

El servicio de selección le permite configurar protocolos para que el visitante determine si puede configurar una cookie en el dispositivo o navegador del usuario al visitar el sitio.

El servicio de selección es una extensión del [servicio Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) , diseñada para controlar si las soluciones de Experience Cloud pueden crear cookies en páginas web para los visitantes antes de su consentimiento. El servicio de selección también le permite establecer protocolos para integrarlos con su plataforma de administración de consentimiento (CMP) y los sistemas existentes como parte del diseño más grande.

Con el servicio de selección, puede especificar si un visitante puede activar las soluciones de Adobe a la vez o presentar soluciones en secuencia para los permisos. Una vez que el cliente completa y registra el proceso de aprobación, puede recuperar las aprobaciones de visitante de CMP desde las soluciones de Adobe.

El servicio de selección se implementa y se configura fácilmente usando [Adobe Launch](https://docs.adobelaunch.com/) con la extensión [de inclusión](../../implementation-guides/opt-in-service/launch.md). También se puede implementar y configurar mediante [la DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

Consulte [el tema Configuración del servicio](../../implementation-guides/opt-in-service/getting-started.md) de selección para comenzar.

>[!NOTE]
>
>El servicio de selección le permite configurar un sistema para aprobar o denegar la descarga de cookies de Adobe solamente. Ni permite recopilar las preferencias de consentimiento de los usuarios ni es un repositorio de preferencias.

>[!IMPORTANT]
>
>El contenido de este documento no es legal y no tiene por qué sustituir al asesoramiento legal. Pida asesoramiento al departamento jurídico de su empresa respecto al consentimiento y las prácticas recomendadas para configurar una implementación de inclusión.

## Inclusión entre soluciones de Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

El servicio de selección es una herramienta para generar una opción de consentimiento en el flujo de trabajo según sus propias necesidades, lo que permite diseñar un flujo de trabajo para reaccionar (etiquetas activadas) antes y después de que el usuario o su controlador de consentimiento reciben consentimiento.

El servicio de selección permite configurar las prácticas de administración de consentimiento para las soluciones de Adobe a:

* Indicar si los requisitos de recopilación de consentimientos se aplican en general a un usuario.
* Especificar qué soluciones tienen permiso para generar cookies.
* Aplicar preferencias predeterminadas para cualquier solución cuya categoría el usuario no haya aceptado o rechazado de forma explícita.
* Activar una respuesta personalizada basada en los cambios en la configuración de consentimiento de un usuario, lo que permite conservar o actualizar la configuración del usuario.

Con los servicios de selección, puede configurar su sitio para permitir que algunas cookies se carguen con previo consentimiento antes de la elección del usuario. Puede configurar los servicios de selección para que los nuevos clientes puedan cargar las cookies después de que el usuario confirme o después de que haya una opción disponible. También puede almacenar y recuperar consentimientos de inclusión desde su plataforma de gestión del consentimiento, o simplemente almacenar los permisos de inclusión en una cookie.

![](assets/Opt-in-approval.png)

A continuación, las soluciones de Adobe pueden comprobar si la etiqueta está aprobada, o pueden suscribirse a los cambios y después recuperar a todos los clientes de Opt-in. El servicio de selección permite obtener permisos directamente a través de las bibliotecas de JavaScript de solución o de ECID si se implementa.
