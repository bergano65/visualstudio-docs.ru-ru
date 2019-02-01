---
title: Xml (динамическое свойство XElement) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779552"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возвращает неформатированное XML-содержимое элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>См. также раздел  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xelement-dynamic-property.md)
