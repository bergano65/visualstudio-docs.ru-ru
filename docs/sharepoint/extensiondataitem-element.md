---
title: Элемент ExtensionDataItem | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c991d3fece3e5997e8d470d168af9eba47c8663
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extensiondataitem-element"></a>Элемент ExtensionDataItem
  Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ значение. Ключ и значение должны быть строками.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|**Key**|Требуется **xs: String** атрибута.<br /><br /> Ключ, используемый для хранения и извлечения элемента данных.|  
|**Значение**|Требуется **xs: String** атрибута.<br /><br /> Значение элемента данных.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта Visual Studio сохраняет данные в новую **ExtensionDataItem** элемент SPDATA-файла для элемента проекта. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  