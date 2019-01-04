---
title: '&lt;formRegions&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 997bd24861f986736d7d691a8d2877f9b5a78566
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909103"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; элемент (Разработка решений Office в Visual Studio)
  `formRegions` Элемент `vstov4` пространство имен содержит области формы Microsoft Office Outlook, связанные с надстройкой VSTO.

## <a name="syntax"></a>Синтаксис

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `formRegions` пространства имен `vstov4` содержит все элементы `formRegion` для надстройки VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.

 В манифесте приложения может быть определен только один элемент `formRegions` .

 У элемента `formRegions` нет атрибутов.

 Элемент `formRegions` имеет следующий элемент.

### <a name="formregion"></a>formRegion
 Является обязательным для надстроек VSTO для Outlook, включающих области форм. `formRegion` Элемент определен в [ &#60;formRegion&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `formRegions` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)