---
title: Элемент FeatureProperties | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26fcdb1dd7fa3b62f7882deb1a077b9466e52018
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325001"
---
# <a name="featureproperties-element"></a>FeatureProperties - элемент
  Коллекция значений свойств, которые входят в состав компонентом при его развертывании в SharePoint. После развертывания функции значения свойств можно использовать в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Необязательный элемент.<br /><br /> Представляет пользовательское свойство, в формате ключ/значение.|  
  
### <a name="parent-elements"></a>Родительские элементы
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент обязательный корневой элемент из `.spdata` файла.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о свойствах компонентов см. в разделе [сведениями упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Сведения об элементе
  
|Элемент|Описание:|  
|-------------|-----------------|  
|**Пространство имен**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## <a name="see-also"></a>См. также
 [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставляют сведения о упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  
