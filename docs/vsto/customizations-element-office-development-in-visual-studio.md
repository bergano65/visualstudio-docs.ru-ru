---
title: '&lt;настройки&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7546b9b5b2d89747aa8557e1b05dc99d99e6bcb
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802099"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;настройки&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `customizations` пространства имен `vstov4` содержит все сведения об установке и загрузке каждого решения Office.

## <a name="syntax-for-document-level-customizations"></a>Синтаксис для настроек уровня документа

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Синтаксис надстроек VSTO

```xml
<customizations>
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
</customizations>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `customizations` содержит конкретные сведения о каждом решении Office. Этот элемент должен принадлежать следующему пространству имен: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Дочерние элементы сборки также необходимо включить в это пространство имен.

 У элемента `customizations` нет атрибутов.

 Элемент `customizations` имеет указанный ниже дочерний элемент.

### <a name="customization"></a>Настройка
 Обязательный. `customization` Элемент в `vstov4` пространство имен определяется в [ &#60;настройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Пример настройки уровня документа

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `customizations` для настройки на уровне документа.

> [!NOTE]
>  Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Пример надстройки VSTO

### <a name="description"></a>Описание:
 В следующем примере кода показано `customizations` элемент для надстройки VSTO. Это надстройка VSTO для Outlook, в которой используются области форм. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
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
</vstov4:customizations>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)