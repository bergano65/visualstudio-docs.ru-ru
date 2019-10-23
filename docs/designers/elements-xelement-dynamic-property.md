---
title: Elements (динамическое свойство XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d92e9ebd1e5be9f3535dcac136bb46ba33975f0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637321"
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

- [Динамические свойства класса XElement](../designers/attribute-xelement-dynamic-property.md)
- [Элемент](../designers/element-xelement-dynamic-property.md)
- [Descendants (динамическое свойство XElement)](../designers/descendants-xelement-dynamic-property.md)