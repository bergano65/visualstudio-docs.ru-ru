---
title: Element (динамическое свойство XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e292be4458459fff2a3784d989e603f21dcb53c9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888066"
---
# <a name="element-xelement-dynamic-property"></a>Element (динамическое свойство XElement)

Получает индексатор, который используется для получения экземпляра дочернего элемента, соответствующего указанному развернутому имени.

## <a name="syntax"></a>Синтаксис

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Индексатор типа `XElement Item(String expandedName)`. Этот индексатор берет параметр развернутого имени и возвращает соответствующее значение элемента <xref:System.Xml.Linq.XElement> или `null`, если элемента с таким именем не существует.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Element%2A> класса <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements (XElement Dynamic Property)](../designers/elements-xelement-dynamic-property.md) (Elements (Динамическое свойство XElement))