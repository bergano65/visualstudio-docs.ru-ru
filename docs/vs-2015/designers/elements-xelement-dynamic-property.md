---
title: Elements (динамическое свойство XElement) | Документация Майкрософт
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
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75cb7f8f6a5259151679ecee84bbeb5db336782f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560360"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Elements (динамическое свойство XElement)](https://docs.microsoft.com/visualstudio/designers/elements-xelement-dynamic-property).  
  
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



