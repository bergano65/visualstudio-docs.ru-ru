---
title: Динамические свойства LINQ to XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 181e9e4fb86a0348c0b5adb1d26a0a4e4e1721bb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970716"
---
# <a name="linq-to-xml-dynamic-properties"></a>Динамические свойства LINQ to XML

В этом разделе приведены справочные сведения о динамических свойствах в LINQ to XML. В частности, эти свойства представляются классами <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые находятся в пространстве имен <xref:System.Xml.Linq>.

Как уже рассказывалось в разделе [Общие сведения о привязке данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), каждое динамическое свойство эквивалентно стандартному открытому свойству или методу в том же классе. В большинстве случаев следует использовать именно эти стандартные методы. Динамические свойства предоставляются специально для привязки данных с помощью LINQ to XML. Дополнительные сведения о стандартных членах этих классов см. в разделах со справочными сведениями <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>.

По разрешаемым ими значениям описанные в этом разделе динамические свойства делятся на две категории:

- Простые, например свойства `Value` в классах <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые разрешаются в одно значение.

- Индексированные значения, например свойства [Elements](../designers/elements-xelement-dynamic-property.md) и [Descendants](../designers/descendants-xelement-dynamic-property.md) класса <xref:System.Xml.Linq.XElement>, которые разрешаются в тип индексатора. Чтобы типы индексатора разрешились в требуемое значение или коллекцию, им необходимо передать параметр развернутого имени.

Все динамические свойства, которые возвращают индексированное значение типа <xref:System.Collections.Generic.IEnumerable%601>, используют отложенное выполнение. Дополнительные сведения об отложенном выполнении см. в разделе [Введение в запросы LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Ссылка

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>См. также

- [Привязка данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Общие сведения о привязке данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Введение в запросы LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
