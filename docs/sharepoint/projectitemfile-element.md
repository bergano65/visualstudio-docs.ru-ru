---
title: Элемент Прожектитемфиле | Документация Майкрософт
description: Получите справочные сведения об элементе Прожектитемфиле, который представляет файл элемента проекта в справочнике по XML-схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7c6dd7fc46dc8616eddc164bcf2ec801657cb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955142"
---
# <a name="projectitemfile-element"></a>ProjectItemFile - элемент
  Представляет файл SharePoint, например файл элемента компонента, для включения в элемент проекта при его развертывании в SharePoint.

## <a name="syntax"></a>Синтаксис

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Тип
 **прожектитемфилетипе**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Источник**|Обязательный атрибут **xs: String** .<br /><br /> Имя файла, который необходимо развернуть с элементом проекта.|
|**Целевой объект**|Необязательный атрибут **xs: String** .<br /><br /> Путь, по которому файл будет развернут в SharePoint относительно корневой папки развертывания. Корневая папка развертывания определяется типом развертывания, указанным в атрибуте **Type** . Если **целевой** атрибут не указан, файл будет развернут в папке с именем, указанным в атрибуте **Source** .<br /><br /> Дополнительные сведения см. в описании свойств **пути развертывания** и **корня развертывания** элементов проекта SharePoint статьи [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Тип**|Обязательный атрибут **xs: String** .<br /><br /> Тип развертывания для файла. Дополнительные сведения о возможных значениях см. в описании свойства " **тип развертывания** " элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Файлы](../sharepoint/files-element.md)|Указывает файлы, включаемые в элемент проекта SharePoint при развертывании в SharePoint.|

## <a name="remarks"></a>Remarks
 Файлы SharePoint, которые обычно указываются в элементах **прожектитемфиле** , включают файлы элементов компонента (*Elements.xml*), файлы схемы для определений списков (*Schema.xml*) и файлы определения веб-части для веб-части (*. WebPart*).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
