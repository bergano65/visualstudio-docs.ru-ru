---
title: "Xml (динамическое свойство XElement) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 3bd6e84a3e59033aeb5050c172439bccbd096082
ms.lasthandoff: 02/22/2017

---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)
Возвращает неформатированное XML-содержимое элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName>, в котором для параметра `SaveOptions` задано значение <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>См. также  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xelement-dynamic-property.md)
