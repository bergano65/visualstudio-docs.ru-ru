---
title: Xml (динамическое свойство XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633522"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)

Возвращает неформатированное XML-содержимое элемента.

## <a name="syntax"></a>Синтаксис

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>См. также

- [Динамические свойства класса XElement](../designers/attribute-xelement-dynamic-property.md)
- [Значение](../designers/value-xelement-dynamic-property.md)