---
title: Files, элемент | Документация Майкрософт
description: Просмотр справочных сведений об элементе Files, который является элементом в схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03473f40bb78c866f3d93dea11a20b8747afad7b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672812"
---
# <a name="files-element"></a>Files - элемент
  Указывает файлы для развертывания с помощью элемента проекта SharePoint, такие как файлы элементов компонента и выходные данные зависимых проектов, не связанных с SharePoint.

## <a name="syntax"></a>Синтаксис

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Тип
 **филеколлектионтипе**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[прожектитемфиле](../sharepoint/projectitemfile-element.md)|Необязательный элемент **прожектитемфилетипе** .<br /><br /> Представляет файл SharePoint, например файл элемента компонента, для включения в элемент проекта при его развертывании в SharePoint.|
|[прожектаутпутфиле](../sharepoint/projectoutputfile-element.md)|Необязательный элемент **прожектаутпутфилетипе** .<br /><br /> Представляет выходные данные проекта, включаемые в элемент проекта при его развертывании в SharePoint.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом `.spdata` файла.|

## <a name="element-information"></a>Сведения об элементе

|Свойство.|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
