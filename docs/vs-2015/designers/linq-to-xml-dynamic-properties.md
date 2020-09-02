---
title: Динамические свойства LINQ to XML | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff0b31512711b8888b05fcfde191c8cb5c47d99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664265"
---
# <a name="linq-to-xml-dynamic-properties"></a>Динамические свойства LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе приведены справочные сведения о динамических свойствах в LINQ to XML. В частности, эти свойства представляются классами <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые находятся в пространстве имен <xref:System.Xml.Linq>.

 Как описано в разделе [Общие сведения о привязке данных WPF к LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), каждое из динамических свойств эквивалентно стандартному открытому свойству или методу в том же классе. В большинстве случаев следует использовать именно эти стандартные методы. Динамические свойства предоставляются специально для связывания данных с помощью LINQ to XML. Дополнительные сведения о стандартных членах этих классов см. в разделах со справочными сведениями <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>.

 По разрешаемым ими значениям описанные в этом разделе динамические свойства делятся на две категории:

- Простые, например свойства `Value` в классах <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые разрешаются в одно значение.

- Индексированные значения, например свойства [Elements](../designers/elements-xelement-dynamic-property.md) и [Descendants](../designers/descendants-xelement-dynamic-property.md) класса <xref:System.Xml.Linq.XElement>, которые разрешаются в тип индексатора. Чтобы типы индексатора разрешились в требуемое значение или коллекцию, им необходимо передать параметр развернутого имени.

  Все динамические свойства, которые возвращают индексированное значение типа <xref:System.Collections.Generic.IEnumerable%601>, используют отложенное выполнение. Дополнительные сведения о отложенном выполнении см. [в разделе Введение в запросы LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>в этом разделе

|Раздел|Описание|
|-----------|-----------------|
|[XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md) (Динамические свойства класса XAttribute)|Содержит сведения о динамических свойствах, представляемых классом <xref:System.Xml.Linq.XAttribute>.|
|[Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)|Содержит сведения о динамических свойствах, представляемых классом <xref:System.Xml.Linq.XElement>.|

## <a name="reference"></a>Справочник
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>См. также:
 [Привязка данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) [привязки данных WPF с обзором LINQ to XML общие сведения о](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [запросах LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
