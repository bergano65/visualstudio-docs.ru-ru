---
title: Attribute (динамическое свойство XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 701636a82b07311bdc9f5a9b20882d613e8469ce
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959950"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (динамическое свойство XElement)

Возвращает индексатор, используемый для получения экземпляра атрибута, соответствующего указанному развернутому имени.

## <a name="syntax"></a>Синтаксис

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Индексатор типа `XAttribute Item(String expandedName)`. Данный индексатор принимает развернутое имя указанного атрибута и возвращает соответствующий <xref:System.Xml.Linq.XAttribute> или значение `null`, если не существует атрибута с указанным именем.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Значение](../designers/value-xattribute-dynamic-property.md)