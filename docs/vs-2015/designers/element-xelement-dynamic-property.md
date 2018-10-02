---
title: Element (динамическое свойство XElement) | Документы Майкрософт
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
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56689506db04ee2aedd484093506db4a4fc7453d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569510"
---
# <a name="element-xelement-dynamic-property"></a>Element (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Element (динамическое свойство XElement)](https://docs.microsoft.com/visualstudio/designers/element-xelement-dynamic-property).  
  
Получает индексатор, который используется для получения экземпляра дочернего элемента, соответствующего указанному развернутому имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Индексатор типа `XElement Item(String expandedName)`. Этот индексатор берет параметр развернутого имени и возвращает соответствующее значение элемента <xref:System.Xml.Linq.XElement> или `null`, если элемента с таким именем не существует.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Element%2A> класса <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Elements (XElement Dynamic Property)](../designers/elements-xelement-dynamic-property.md) (Elements (Динамическое свойство XElement))



