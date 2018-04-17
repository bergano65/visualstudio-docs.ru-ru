---
title: Файлы элемент | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d75041c1b0202eecd5769773efbcfce9c53ec4ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="files-element"></a>Элемент Files
  Указывает файлы для развертывания с элементом проекта SharePoint, например элементов компонента файлов и выходных данных зависимого вне SharePoint проектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>Тип  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Необязательный **ProjectItemFileType** элемента.<br /><br /> Представляет файл SharePoint, таких как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Необязательный **ProjectOutputFileType** элемента.<br /><br /> Представляет выходные данные проекта для включения с элементом проекта при его развертывании в SharePoint.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Это обязательный корневой элемент SPDATA-файла.|  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  