---
title: '&lt;formRegion&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 33bc2ce58f90f37a1219427558a01bd13e5654df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414545"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; элемент (Разработка решений Office в Visual Studio)
  `formRegion` Элемент `vstov4` пространство имен определяет область формы Microsoft Office Outlook, связанный с надстройкой VSTO.

## <a name="syntax"></a>Синтаксис

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `formRegion` пространства имен `vstov4` определяет область формы, связанную с надстройкой VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.

 Для одной и той же надстройки VSTO можно определить несколько элементов `formRegion` в рамках элемента `formRegions` .

 Элемент `formRegion` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный. Определяет имя области формы.|

 Элемент `formRegion` имеет указанные ниже дочерние элементы.

### <a name="messageclass"></a>messageClass
 Элемент `messageClass` определяет форму Outlook, которая связана с областью формы.

 Элемент `messageClass` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный. Определяет форму, которая связана с областью формы.|

## <a name="example"></a>Пример
 В приведенном ниже примере кода показан элемент `formRegion` манифеста приложения для надстройки VSTO для Outlook, развертываемой с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Имеется три класса сообщений, связанных с одной и той же областью формы. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>См. также

- [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)