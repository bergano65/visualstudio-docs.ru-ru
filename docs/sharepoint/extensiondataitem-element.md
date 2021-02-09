---
title: Элемент Екстенсиондатаитем | Документация Майкрософт
description: Просмотр справочных сведений об элементе Екстенсиондатаитем, который является элементом в схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: add1a119283635f9cfd9bebddfe18228f1976703
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876827"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem - элемент
  Пользовательский элемент данных, связанный с элементом проекта SharePoint в формате "ключ — значение". Ключ и значение должны быть строками.

## <a name="syntax"></a>Синтаксис

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Ключ**|Обязательный атрибут **xs: String** .<br /><br /> Ключ, используемый для хранения и извлечения элемента данных.|
|**Значение**|Обязательный атрибут **xs: String** .<br /><br /> Значение элемента данных.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|

## <a name="remarks"></a>Remarks
 При связывании пользовательских данных с элементом проекта SharePoint с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта Visual Studio сохраняет данные в новый элемент **екстенсиондатаитем** в `.spdata` файле для элемента проекта. Дополнительные сведения см. [в разделе Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
