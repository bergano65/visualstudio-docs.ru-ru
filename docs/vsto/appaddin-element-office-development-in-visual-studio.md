---
title: '&lt;&gt;элемент аппаддин (разработка решений Office в Visual Studio)'
description: Сведения о том, как элемент Аппаддин пространства имен vstov4 хранит сведения о настройках для надстроек VSTO.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 427d7bc0ec59b98394b292745985be7fdf69b904
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950514"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент аппаддин (разработка решений Office в Visual Studio)
  Элемент **аппаддин** `vstov4` пространства имен хранит сведения о настройках для надстроек VSTO.

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
 Элемент **аппаддин** является обязательным и находится в `vstov4` пространстве имен. В манифесте приложения определен только один элемент **аппаддин** .

 Элемент **аппаддин** имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|**приложение**|Обязательный элемент. Идентифицирует приложение Microsoft Office. Может иметь одно из следующих значений: Excel, InfoPath, Outlook, PowerPoint, Project, Visio или Word.|
|**loadBehavior**|Необязательный элемент. По умолчанию **LoadBehavior** включается путем присвоения этому значению значения. Для отладки надстройку VSTO можно отключить, задав значение 2. Дополнительные сведения см. в таблице значения LoadBehavior в [записях реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Обязательный элемент. Это значение является именем раздела реестра, который будет использоваться приложением для загрузки надстройки VSTO. Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 Элемент **аппаддин** имеет следующие дочерние элементы.

### <a name="friendlyname"></a>friendlyName
 Необязательный элемент. Элемент **FriendlyName** объясняется в [&#60;friendlyName&#62; элемент &#40;разработке решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 Необязательный элемент. Элемент **Description** объясняется в [&#60;description&#62; элемент &#40;разработке решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Является обязательным только для надстроек VSTO для Outlook, включающих области форм. Элемент **формрегионс** объясняется в [&#60;формрегионс&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В следующем примере кода показаны элементы **аппаддин** в решении Outlook, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

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