---
title: Xml (динамическое свойство XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843957"
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

- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Значение](../designers/value-xelement-dynamic-property.md)