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
ms.openlocfilehash: eb88c8adc3f32e428543e2bf1e0e80e9538678a2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766511"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem - элемент
  Пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ значение. Ключ и значение должны быть строками.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Key**|Требуется **xs: строка** атрибута.<br /><br /> Ключ, используемый для хранения и извлечения элемента данных.|  
|**Значение**|Требуется **xs: String** атрибута.<br /><br /> Значение элемента данных.|  
  
### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта Visual Studio сохраняет данные в новую **ExtensionDataItem** элемент `.spdata` в файле элемент проекта. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Сведения об элементе
  
|||  
|-|-|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
