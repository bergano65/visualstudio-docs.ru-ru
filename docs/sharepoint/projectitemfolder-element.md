---
title: Элемент ProjectItemFolder | Документация Майкрософт
description: Получите справочные сведения об элементе ProjectItemFolder, который представляет сопоставленную папку в справочнике по XML-схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d1a5b5086ef90b9d8399a6f0f76bdee77c07288e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950579"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder - элемент
  Представляет сопоставленную папку.

## <a name="syntax"></a>Синтаксис

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Тип
 **прожектитемфолдертипе**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Цель**|Обязательный атрибут **xs: String** .<br /><br /> Путь к папке в установке SharePoint, которой соответствует сопоставленная папка, относительно корневой папки развертывания. Корневая папка развертывания определяется типом развертывания, указанным в атрибуте **Type** .<br /><br /> Дополнительные сведения см. в описании свойств **пути развертывания** и **корня развертывания** элементов проекта SharePoint статьи [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Тип**|Обязательный атрибут **xs: String** .<br /><br /> Тип развертывания для сопоставленной папки. Дополнительные сведения о возможных значениях см. в описании свойства " **тип развертывания** " элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом для файла *данных..*|

## <a name="remarks"></a>Remarks
 Дополнительные сведения о сопоставленных папках см. [в разделе инструкции. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/2010/<br>Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Как добавлять и удалять сопоставленные папки](../sharepoint/how-to-add-and-remove-mapped-folders.md)
