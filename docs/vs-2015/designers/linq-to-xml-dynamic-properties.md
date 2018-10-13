---
title: Динамические свойства LINQ to XML | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b16ff8a5969282f2c062c19fed84292f0755d0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212424"
---
# <a name="linq-to-xml-dynamic-properties"></a>Динамические свойства LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе приведены справочные сведения о динамических свойствах в LINQ to XML. В частности, эти свойства представляются классами <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые находятся в пространстве имен <xref:System.Xml.Linq>.  
  
 Как уже рассказывалось в разделе [Общие сведения о привязке данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), каждое динамическое свойство эквивалентно стандартному открытому свойству или методу в том же классе. В большинстве случаев следует использовать именно эти стандартные методы. Динамические свойства предоставляются специально для привязки данных с помощью LINQ to XML. Дополнительные сведения о стандартных членах этих классов см. в разделах со справочными сведениями <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>.  
  
 По разрешаемым ими значениям описанные в этом разделе динамические свойства делятся на две категории:  
  
-   Простые, например свойства `Value` в классах <xref:System.Xml.Linq.XAttribute> и <xref:System.Xml.Linq.XElement>, которые разрешаются в одно значение.  
  
-   Индексированные значения, например свойства [Elements](../designers/elements-xelement-dynamic-property.md) и [Descendants](../designers/descendants-xelement-dynamic-property.md) класса <xref:System.Xml.Linq.XElement>, которые разрешаются в тип индексатора. Чтобы типы индексатора разрешились в требуемое значение или коллекцию, им необходимо передать параметр развернутого имени.  
  
 Все динамические свойства, которые возвращают индексированное значение типа <xref:System.Collections.Generic.IEnumerable%601>, используют отложенное выполнение. Дополнительные сведения об отложенном выполнении см. в разделе [Введение в запросы LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Динамические свойства класса XAttribute](../designers/xattribute-class-dynamic-properties.md)|Содержит сведения о динамических свойствах, представляемых классом <xref:System.Xml.Linq.XAttribute>.|  
|[Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)|Содержит сведения о динамических свойствах, представляемых классом <xref:System.Xml.Linq.XElement>.|  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>См. также  
 [Привязка данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Общие сведения о привязке данных WPF с помощью LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Введение в запросы LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)



