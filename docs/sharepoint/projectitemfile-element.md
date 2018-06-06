---
title: Projectitemfile-элемент | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 60ae46f981bc0377c93f1e00d09094604b5d776c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34694008"
---
# <a name="projectitemfile-element"></a>Элемент ProjectItemFile
  Представляет файл SharePoint, таких как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Тип  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Источник**|Требуется **xs: String** атрибута.<br /><br /> Имя файла, который развертывается с элементом проекта.|  
|**Целевой объект**|Необязательный **xs: String** атрибута.<br /><br /> Путь, где будет развернут файл на сайте SharePoint, относительно корневой папки развертывания. Корневой папки развертывания определяется типом развертывания, заданные **тип** атрибута. Если **целевой** атрибут не указан, файл будет развернут в папку с именем, указанным в **источника** атрибута.<br /><br /> Дополнительные сведения см. в разделе описания **путь развертывания** и **корневого каталога развертывания** свойства SharePoint элементами проекта в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Тип развертывания файла. Дополнительные сведения о возможных значениях см. в описании для **тип развертывания** свойства элементов проекта SharePoint в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Файлы](../sharepoint/files-element.md)|Указывает файлы, включаемые в элемент проекта SharePoint при его развертывании в SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 Файлы SharePoint, которые обычно используются в **ProjectItemFile** элементы включают элементов компонента файлов (Elements.xml), файлы схемы для определения списков (Schema.xml) и файлы определений веб-части для веб-части (.webpart).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  