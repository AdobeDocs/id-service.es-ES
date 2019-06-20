---
description: Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.
keywords: Servicio de ID
seo-description: Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.
seo-title: Escenarios de migración del servicio Experience Cloud ID
title: Escenarios de migración del servicio Experience Cloud ID
uuid: 9 e 229045-6508-48 c 4-ae 39-9537 b 4941853
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Escenarios de migración del servicio Experience Cloud ID {#experience-cloud-id-service-migration-scenarios}

Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.

## Propiedad web única {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Empresa de Ejemplo S.A.
* **Habilitación de Experience Cloud**: no
* **Propiedades web**: example.com
* **Servidores de recopilación de datos**: metrics.example.com, smetrics.example.com
* **Archivo JavaScript de Analytics**: un único archivo para todas las páginas del sitio

En primer lugar, debe habilitarse Experience Cloud para este cliente (consulte los [requisitos](../../reference/requirements.md)). Y, dado que cuenta con un solo archivo JavaScript, este cliente no necesita un período de gracia. Este cliente también configurará la migración de visitantes y dejará de utilizar su CNAME de recopilación de datos, que no es necesario.

## Varios archivos JavaScript, etiquetas de imagen predefinidas en el código {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Otra Empresa de Ejemplo S.A.
* **Habilitación de Experience Cloud**: sí
* **Propiedades web**: anotherexample.com
* **Servidores de recopilación de datos**: anotherexampleco.112.2o7.net
* **Archivo JavaScript de Analytics**: varios archivos JavaScript. Un archivo para el sitio principal y otro archivo para la sección de soporte técnico que se conserva en un CMS independiente.
* **Otros métodos de recopilación de datos**: etiquetas de imagen predefinidas en el código en una única sección del sitio

En primer lugar, este cliente debe buscar su ID de organización de Adobe Experience Cloud (consulte los [requisitos](../../reference/requirements.md)). A continuación, deberá configurar un período de gracia de migración porque está utilizando varios archivos JavaScript. This customer will also set up visitor migration and then migrate from `*.2o7.net` to `*.sc.omtrdc.net`.

Cuando este cliente actualice el código JavaScript de Analytics a la versión más reciente como preparación para la implementación del servicio de ID de [!DNL Experience Cloud], también actualizará todas las etiquetas de imagen predefinidas en el código para que utilicen JavaScript en su lugar.

## Varias propiedades web, varios archivos JavaScript y reproductor de vídeos basado en Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: Buen Cliente S.A.
* **Habilitación de Experience Cloud**: sí
* **Propiedades web**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Servidores de recopilación de datos**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Archivo JavaScript de Analytics**: varios archivos JavaScript. Un archivo por cada propiedad web.
* **Otros métodos de recopilación de datos**: un reproductor de vídeos basado en Flash

En primer lugar, este cliente debe buscar su ID de organización de Adobe Experience Cloud (consulte los [requisitos](../../reference/requirements.md)). A continuación, deberá configurar un período de gracia de migración porque está utilizando varios archivos JavaScript. Este cliente hace un seguimiento de los visitantes entre el dominio principal y los subdominios, de modo que seguirá utilizando el CNAME de recopilación de datos con el servicio de ID de visitante.

Cuando este cliente actualice el código JavaScript de Analytics a la versión más reciente como preparación para la implementación del servicio de ID de [!DNL Experience Cloud], también actualizará el reproductor de vídeos basado en Flash a la última versión de AppMeasurement para Flash.
