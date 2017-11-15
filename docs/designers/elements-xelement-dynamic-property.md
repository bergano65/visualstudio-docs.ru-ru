---
title: "Elements (динамическое свойство XElement) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b28407d0b69d1ac7e2309ee1f8c24393b68e84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="elements-xelement-dynamic-property"></a>Elements (динамическое свойство XElement)
Получает индексатор, который используется для извлечения дочернего элемента текущего элемента с заданным развернутым именем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Индексатор принимает развернутое имя нужных дочерних элементов и возвращает соответствующие дочерние элементы в коллекцию <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Примечания  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.  
  
 Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.  
  
 В данном свойстве используется отложенное выполнение.  
  
## <a name="see-also"></a>См. также  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Elements (XElement Dynamic Property)](../designers/element-xelement-dynamic-property.md)  (Elements (Динамическое свойство XElement))  
 [Descendants (динамическое свойство XElement)](../designers/descendants-xelement-dynamic-property.md)