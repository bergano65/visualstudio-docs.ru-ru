---
title: Elements (динамическое свойство XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff2071ba71d60db87332b0e23948d63ac1b2289
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913201"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (динамическое свойство XElement)

Получает индексатор, который используется для извлечения дочернего элемента текущего элемента с заданным развернутым именем.

## <a name="syntax"></a>Синтаксис

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Индексатор принимает развернутое имя нужных дочерних элементов и возвращает соответствующие дочерние элементы в коллекцию <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.

Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.

В данном свойстве используется отложенное выполнение.

## <a name="see-also"></a>См. также

- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Элемент](../designers/element-xelement-dynamic-property.md)
- [Descendants (динамическое свойство XElement)](../designers/descendants-xelement-dynamic-property.md)