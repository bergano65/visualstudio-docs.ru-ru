---
title: Xml (динамическое свойство XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b895865485ca3ac110670cd9d123d9a8c18ee8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925616"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)

Возвращает неформатированное XML-содержимое элемента.

## <a name="syntax"></a>Синтаксис

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>См. также

- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Значение](../designers/value-xelement-dynamic-property.md)