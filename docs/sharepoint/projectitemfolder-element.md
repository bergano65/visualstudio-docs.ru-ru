---
title: Projectitemfolder-элемент | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3509588baa700cc6d280c01c2456b4736b8eb58d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691876"
---
# <a name="projectitemfolder-element"></a>Элемент ProjectItemFolder
  Представляет сопоставленную папку.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Тип  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Целевой объект**|Требуется **xs: строка** атрибута.<br /><br /> Путь к папке в установке SharePoint, соответствующий сопоставленную папку, относительно корневой папки развертывания. Корневой папки развертывания определяется типом развертывания, заданные **тип** атрибута.<br /><br /> Дополнительные сведения см. в разделе описания **путь развертывания** и **корневого каталога развертывания** свойства SharePoint элементами проекта в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Тип развертывания для сопоставленной папки. Дополнительные сведения о возможных значениях см. в описании для **тип развертывания** свойства элементов проекта SharePoint в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневой элемент `.spdata` файла.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о сопоставленных папок см. в разделе [как: Добавление и удаление папок Mapped](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Практическое руководство. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  