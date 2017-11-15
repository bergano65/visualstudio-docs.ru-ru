---
title: "Xml (динамическое свойство XElement) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed9aaee4e227627cf9ef5030863701445671444b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>См. также  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xelement-dynamic-property.md)