---
title: Elements (динамическое свойство XElement) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 158e200a33b4783df9f63f42a1eca7bb8957d449
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145685"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Получает индексатор, который используется для извлечения дочернего элемента текущего элемента с заданным развернутым именем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Индексатор принимает развернутое имя нужных дочерних элементов и возвращает соответствующие дочерние элементы в коллекцию <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.  
  
 Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.  
  
 В данном свойстве используется отложенное выполнение.  
  
## <a name="see-also"></a>См. также  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Elements (XElement Dynamic Property)](../designers/element-xelement-dynamic-property.md)  (Elements (Динамическое свойство XElement))  
 [Descendants (динамическое свойство XElement)](../designers/descendants-xelement-dynamic-property.md)
