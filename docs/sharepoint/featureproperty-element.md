---
title: Элемент FeatureProperty | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2ff9571adc23c9ddc86de96736b9d37ef1cec5d3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691822"
---
# <a name="featureproperty-element"></a>Элемент FeatureProperty
  Представляет пользовательское свойство, которое входит в состав компонентом при его развертывании в SharePoint. После развертывания функции свойства можно использовать в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
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
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  