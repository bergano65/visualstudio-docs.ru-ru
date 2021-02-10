---
title: '&lt;&gt;элемент формрегионс (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970339"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент формрегионс (разработка решений Office в Visual Studio)
  `formRegions`Элемент `vstov4` пространства имен содержит Microsoft Office области формы Outlook, связанные с надстройкой VSTO.

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
 Является обязательным для надстроек VSTO для Outlook, включающих области форм. `formRegion`Элемент определяется в [&#60;формрегион&#62; элемента &#40;разработки Office в&#41;Visual Studio ](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `formRegions` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

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