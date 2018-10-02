---
title: Value (динамическое свойство XAttribute) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: af8f122bfbf2ce37b161afb5f0665a9677ef2f3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570798"
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Value (динамическое свойство XAttribute)](https://docs.microsoft.com/visualstudio/designers/value-xattribute-dynamic-property).  
  
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



