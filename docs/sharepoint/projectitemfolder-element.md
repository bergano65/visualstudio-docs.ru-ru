---
title: Элемент ProjectItemFolder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539819"
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

|Атрибут|Описание:|
|---------------|-----------------|
|**Целевой объект**|Обязательный атрибут **xs: String** .<br /><br /> Путь к папке в установке SharePoint, которой соответствует сопоставленная папка, относительно корневой папки развертывания. Корневая папка развертывания определяется типом развертывания, указанным в атрибуте **Type** .<br /><br /> Дополнительные сведения см. в описании свойств **пути развертывания** и **корня развертывания** элементов проекта SharePoint статьи [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Обязательный атрибут **xs: String** .<br /><br /> Тип развертывания для сопоставленной папки. Дополнительные сведения о возможных значениях см. в описании свойства " **тип развертывания** " элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом для файла *данных..*|

## <a name="remarks"></a>Примечания
 Дополнительные сведения о сопоставленных папках см. [в разделе инструкции. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство.|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/2010/<br>Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Как добавлять и удалять сопоставленные папки](../sharepoint/how-to-add-and-remove-mapped-folders.md)
