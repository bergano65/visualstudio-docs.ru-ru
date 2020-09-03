---
title: '&lt;&gt;элемент настройки (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1239c6749f25bf4bce7a1f5cc89a2a8430c98a4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544876"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент настройки (разработка решений Office в Visual Studio)
  Элемент `customization` пространства имен `vstov4` описывает конкретное решение Office. Дочерние элементы настроек уровня документа и надстроек VSTO отличаются друг от друга.

## <a name="syntax-for-document-level-customizations"></a>Синтаксис для настроек на уровне документа

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Синтаксис надстроек VSTO

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `customization` содержит сведения о настройках. Этот элемент должен принадлежать следующему пространству имен: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Существует по одному элементу `customization` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `customization` .

 Дочерние элементы сборки также необходимо включить в это пространство имен.

 Элемент `customization` имеет указанный ниже атрибут.

|Атрибут|Описание:|
|---------------|-----------------|
|`id`|Требуется для многопроектного развертывания. Элемент `id` уникальным образом идентифицирует решение Office.|

### <a name="document-level-customizations"></a>Настройки на уровне документа
 Элемент `customization` имеет указанный ниже дочерний элемент.

#### <a name="document"></a>документ
 `document`Элемент в `vstov4` пространстве имен определяется в [элементе&#60;Document&#62; &#40;разработки Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Надстройки VSTO
 Элемент `customization` имеет указанный ниже дочерний элемент.

#### <a name="appaddin"></a>appAddin
 `appAddin`Элемент в `vstov4` пространстве имен определяется в [&#60;аппаддин&#62; элемент &#40;разработки решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `customization` для настройки на уровне документа. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Пример надстройки VSTO

### <a name="description"></a>Описание:
 В следующем примере кода показан `customization` элемент для надстройки VSTO. Это надстройка VSTO для Outlook, в которой используются области форм. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)