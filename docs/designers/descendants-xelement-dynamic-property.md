---
title: Descendants (динамическое свойство XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d3e173ff0b1cfc6058090593a351660128082c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012538"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (динамическое свойство XElement)

Возвращает индексатор, который используется для получения всех элементов-потомков текущего элемента, соответствующих заданному развернутому имени.

## <a name="syntax"></a>Синтаксис

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Этот индексатор принимает развернутое имя указанных элементов-потомков и возвращает соответствующие дочерние элементы в коллекции <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.

Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.

В данном свойстве используется отложенное выполнение.

## <a name="see-also"></a>См. также

- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements (XElement Dynamic Property)](../designers/elements-xelement-dynamic-property.md) (Elements (Динамическое свойство XElement))