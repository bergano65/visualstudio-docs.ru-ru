---
title: Value (динамическое свойство XAttribute) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757547"
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
  
## <a name="see-also"></a>См. также раздел  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md)  (Динамические свойства класса XAttribute)  
 [Attribute (XElement Dynamic Property)](../designers/attribute-xelement-dynamic-property.md) (Attribute (динамическое свойство XElement))
