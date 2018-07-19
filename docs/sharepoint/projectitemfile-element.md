---
title: Элемент ProjectItemFile | Документация Майкрософт
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
ms.openlocfilehash: 0b66849f9df9ed4de7725bca842c38f4f5a52582
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119894"
---
# <a name="projectitemfile-element"></a>ProjectItemFile - элемент
  Представляет файл SharePoint, такие как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Тип  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Источник**|Требуется **xs: String** атрибута.<br /><br /> Имя файла, который развертывается с элементом проекта.|  
|**Целевой объект**|Необязательный **xs: String** атрибута.<br /><br /> Путь, где этот файл будет развернут на сайте SharePoint, относительно корневой папки развертывания. Корневой папки развертывания определяется типом развертывания, заданные **тип** атрибута. Если **целевой** атрибут не указан, файл будет развернут в папку с именем, указанным в **источника** атрибута.<br /><br /> Дополнительные сведения см. в разделе описания **путь развертывания** и **Deployment Root** свойства SharePoint элементами проекта в среде [решения разработки SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Тип развертывания файла. Дополнительные сведения о возможных значениях см. в описании для **тип развертывания** свойства элементов проекта SharePoint в [решения разработки SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Файлы](../sharepoint/files-element.md)|Указывает файлы, включаемые с элементом проекта SharePoint при развертывании в SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 Файлы SharePoint, которые обычно указывается в **ProjectItemFile** элементы включают элемент файлы компонентов (*Elements.xml*), файлы схемы для определения списков (*Schema.xml*) и файлов определения веб-части для веб-частей (*.webpart*).  
  
## <a name="element-information"></a>Сведения об элементе
  
|||  
|-|-|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## <a name="see-also"></a>См. также
 [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
