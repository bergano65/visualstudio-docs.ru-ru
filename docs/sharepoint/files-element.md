---
title: Файлы элемент | Документация Майкрософт
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
ms.openlocfilehash: 1cf64fc8f70c0a3cf3ed5df1237603f490a703db
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639574"
---
# <a name="files-element"></a>Files - элемент
  Указывает файлы для развертывания с элементом проекта SharePoint, например элементов компонента файлов и выходных данных зависимого вне SharePoint проектов.

## <a name="syntax"></a>Синтаксис

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Тип
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание:|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Необязательный **ProjectItemFileType** элемент.<br /><br /> Представляет файл SharePoint, такие как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Необязательный **ProjectOutputFileType** элемент.<br /><br /> Представляет выходные данные проекта для включения с элементом проекта при его развертывании в SharePoint.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент обязательный корневой элемент из `.spdata` файла.|

## <a name="element-information"></a>Сведения об элементе

|||
|-|-|
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|ProjectItemModelSchema.xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
- [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
