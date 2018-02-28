---
title: "Элемент ExtensionData | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: aafabb1d481afe41dd3dc932a176f6674bae6f99
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="extensiondata-element"></a>Элемент ExtensionData
  Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Необязательный элемент.<br /><br /> Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ значение. Ключ и значение должны быть строками.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Это обязательный корневой элемент SPDATA-файла.|  
  
## <a name="remarks"></a>Примечания  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта Visual Studio сохраняет данные для **ExtensionData** элемент SPDATA-файла для элемента проекта. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  