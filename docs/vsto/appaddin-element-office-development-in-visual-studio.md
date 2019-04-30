---
title: '&lt;appAddin&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2116576acb06e6291749d9c0176fcf4ebb426739
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953248"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; элемент (Разработка решений Office в Visual Studio)
  **AppAddin** элемент `vstov4` пространство имен хранит сведения о настройках для надстроек VSTO.

## <a name="syntax"></a>Синтаксис

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 **AppAddin** элемент является обязательным и находится в `vstov4` пространства имен. Имеется только один **appAddin** элементу, определенному в манифесте приложения.

 **AppAddin** элемент имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|**Приложения**|Обязательный. Идентифицирует приложение Microsoft Office. Он может иметь одно из следующих значений: Excel, InfoPath, Outlook, PowerPoint, Project, Visio или Word.|
|**loadBehavior**|Необязательный параметр. По умолчанию **loadBehavior** можно включить, задав этого значения. Для отладки надстройку VSTO можно отключить, задав значение 2. Дополнительные сведения см. в таблице, в [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Обязательный. Это значение является именем раздела реестра, который будет использоваться приложением для загрузки надстройки VSTO. Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 **AppAddin** элемент имеет следующие дочерние элементы.

### <a name="friendlyname"></a>friendlyName
 Необязательный параметр. **FriendlyName** элементы объяснены на [ &#60;friendlyName&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>Описание
 Необязательный параметр. **Описание** элементы объяснены на [ &#60;описание&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Является обязательным только для надстроек VSTO для Outlook, включающих области форм. **FormRegions** элементы объяснены на [ &#60;formRegions&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В следующем примере кода показано **appAddin** элементов в решении Outlook, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
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
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)