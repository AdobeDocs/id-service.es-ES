---
description: Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.
keywords: Servicio de ID
seo-description: Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.
seo-title: Escenarios de migración del servicio de identidad de Experience Cloud
title: Escenarios de migración del servicio de Experience Cloud ID
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Escenarios de migración del servicio de identidad de Experience Cloud {#experience-cloud-id-service-migration-scenarios}

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

En primer lugar, este cliente debe buscar su ID de organización de Adobe Experience Cloud (consulte los [requisitos](../../reference/requirements.md)). A continuación, deberá configurar un período de gracia de migración porque está utilizando varios archivos JavaScript. Este cliente también configurará la migración de visitantes y cambiará de `*.2o7.net` a `*.sc.omtrdc.net`.

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
