---
title: Элемент Прожектаутпутфиле | Документация Майкрософт
description: Получите справочные сведения об элементе Прожектаутпутфиле, который представляет выходные данные отдельного проекта в справочнике по XML-схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a3b5a0f6474231fdc8f7617040ec4aa57056d9c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966959"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile - элемент
  Представляет выходные данные отдельного проекта, включаемые в элемент проекта при его развертывании в SharePoint.

## <a name="syntax"></a>Синтаксис

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Тип
 **прожектаутпутфилетипе**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**ProjectId**|Обязательный атрибут **xs: String** .<br /><br /> Идентификатор GUID зависимого проекта, который содержит выходные данные, которые необходимо включить. Это соответствует элементу **прожектгуид** в файле зависимого проекта.|
|**ProjectPath**|Обязательный атрибут **xs: String** .<br /><br /> Относительный путь, включая имя файла проекта зависимого проекта, который содержит выходные данные, которые необходимо включить. Этот путь задается относительно корневой папки проекта SharePoint, содержащего элемент проекта SharePoint.|
|**Целевой объект**|Необязательный атрибут **xs: String** .<br /><br /> Путь, по которому должны развертываться зависимые выходные данные проекта на сервере SharePoint относительно корневой папки развертывания. Корневая папка развертывания определяется типом развертывания, указанным в атрибуте **Type** .<br /><br /> Дополнительные сведения см. в описании свойств **пути развертывания** и **корня развертывания** элементов проекта SharePoint статьи [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Тип**|Обязательный атрибут **xs: String** .<br /><br /> Тип развертывания, используемый для выходных данных зависимого проекта. Дополнительные сведения о возможных значениях см. в описании свойства " **тип развертывания** " элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Файлы](../sharepoint/files-element.md)|Указывает файлы, включаемые в элемент проекта SharePoint при развертывании в SharePoint.|

## <a name="remarks"></a>Remarks
 Используйте элемент **прожектаутпутфиле** для включения выходных данных проекта в развертывание элемента проекта SharePoint. Можно указать другой проект или тот же проект, который содержит элемент проекта. Дополнительные сведения см. [в разделе Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
