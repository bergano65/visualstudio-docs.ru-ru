---
title: Элемент SafeControls | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08f981c5dbbf5ae380e782c03553a8f249f41e2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="safecontrols-element"></a>Элемент SafeControls
  Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Необязательный элемент.<br /><br /> Представляет элемент управления ASPX или веб-части, которые обозначены как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Это обязательный корневой элемент SPDATA-файла.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о безопасных элементов управления см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  