---
title: Элемент ExtensionData | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 815846ad310fa32ebcd3195806956cb34e40fd86
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876178"
---
# <a name="extensiondata-element"></a>ExtensionData - элемент
  Представляет коллекцию пользовательских элементов данных, которые связаны с элементом проекта SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Необязательный элемент.<br /><br /> Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ/значение. Ключ и значение должны быть строками.|  
  
### <a name="parent-elements"></a>Родительские элементы
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент обязательный корневой элемент из `.spdata` файла.|  
  
## <a name="remarks"></a>Примечания  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта, Visual Studio сохраняет данные для **ExtensionData** элемент `.spdata` файл проекта элемент. Дополнительные сведения см. в разделе [сохранения данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Сведения об элементе
  
|||  
|-|-|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## <a name="see-also"></a>См. также
 [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
