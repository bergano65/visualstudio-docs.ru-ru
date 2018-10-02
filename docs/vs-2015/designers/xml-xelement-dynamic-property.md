---
title: Xml (динамическое свойство XElement) | Документация Майкрософт
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
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561905"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Xml (динамическое свойство XElement)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property).  
  
Возвращает неформатированное XML-содержимое элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>См. также  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xelement-dynamic-property.md)



