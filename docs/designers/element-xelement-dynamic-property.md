---
title: Element (динамическое свойство XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637325"
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
- [Динамические свойства класса XElement](../designers/attribute-xelement-dynamic-property.md)
- [Elements (XElement Dynamic Property)](../designers/elements-xelement-dynamic-property.md) (Elements (Динамическое свойство XElement))