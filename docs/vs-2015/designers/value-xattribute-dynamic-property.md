---
title: Value (динамическое свойство XAttribute) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd9ea1fa163980a39bcd9981b9e1d757d72fcb6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229155"
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Получает или устанавливает значение атрибута XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Объект типа <xref:System.String>, содержащий значение этого атрибута.  
  
## <a name="exceptions"></a>Исключения  
  
|Тип исключения|Условие|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|При настройке значение параметра `value` - `null`.|  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно свойству <xref:System.Xml.Linq.XAttribute.Value%2A> класса <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, однако это динамическое свойство также поддерживает уведомление об изменениях.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md)  (Динамические свойства класса XAttribute)  
 [Attribute (XElement Dynamic Property)](../designers/attribute-xelement-dynamic-property.md) (Attribute (динамическое свойство XElement))



