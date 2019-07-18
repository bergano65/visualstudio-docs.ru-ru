---
title: Элемент SafeControls | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce943416bba84c46ce7b709c3d2bdb6ddb3e4447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009562"
---
# <a name="safecontrols-element"></a>SafeControls - элемент
  Коллекция элементов управления ASPX и веб-частей, которые обозначены как безопасные для любого пользователя, для доступа к на любой странице ASPX на сайте SharePoint.

## <a name="syntax"></a>Синтаксис

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Необязательный элемент.<br /><br /> Представляет элемент управления ASPX или веб-части, которое обозначается как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент обязательный корневой элемент из *.spdata* файла.|

## <a name="remarks"></a>Примечания
 Дополнительные сведения о безопасных элементов управления, см. в разделе [сведениями упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|||
|-|-|
|**Пространство имен**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|ProjectItemModelSchema.xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
- [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставляют сведения о упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
