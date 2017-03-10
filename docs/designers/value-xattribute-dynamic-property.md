---
title: "Value (динамическое свойство XAttribute) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c013001a52e5b894bcbcdaf9a40309505b39140c
ms.lasthandoff: 02/22/2017

---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)
Получает или устанавливает значение атрибута XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Объект <xref:System.String>, содержащий значение этого атрибута.  
  
## <a name="exceptions"></a>Исключения  
  
|Тип исключения|Условие|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|При настройке значение параметра `value` - `null`.|  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно свойству <xref:System.Xml.Linq.XAttribute.Value%2A> класса <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, но это динамическое свойство также поддерживает уведомления об изменениях.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md)  (Динамические свойства класса XAttribute)  
 [Attribute (XElement Dynamic Property)](../designers/attribute-xelement-dynamic-property.md) (Attribute (динамическое свойство XElement))
