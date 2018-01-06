---
title: "Элемент FeatureProperty | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: FeatureProperty element
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0f1576c23b409226501637ada8d12d2320dd3c37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="featureproperty-element"></a>Элемент FeatureProperty
  Представляет пользовательское свойство, которое входит в состав компонентом при его развертывании в SharePoint. После развертывания функции свойства можно использовать в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Key**|Требуется **xs: String** атрибута.<br /><br /> Ключ, используемый для хранения и извлечения значения свойства. Каждое свойство должно иметь ключ, который является уникальным в пределах компонента.|  
|**Значение**|Требуется **xs: String** атрибута.<br /><br /> Значение свойства.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, которые входят в состав компонентом при его развертывании в SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о свойствах компонентов см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  