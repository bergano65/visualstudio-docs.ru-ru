---
title: "Value (динамическое свойство XAttribute) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d647e7623820c6621f6605277a695a98454fec5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)
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