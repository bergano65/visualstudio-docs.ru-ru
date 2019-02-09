---
title: Средства XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d07e7d2a1a8d96b19354ea8d1261b2e82a84d3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946901"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio

*Расширяемый язык разметки (XML)* — это язык разметки, позволяющий описывать данные. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML, используются таблицы стилей например Extensible Stylesheet Language (XSL) и каскадных таблиц стилей (CSS) для представления данных в браузере. XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.

XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений и поставщиков.

XML лежит в основе многих возможностей Visual Studio и .NET Framework. Перечисленные ниже статьи названия, средств и функций, связанных с XML, которые предлагаются в Visual Studio и .NET Framework.

Дополнительные сведения см. в разделе <xref:System.Xml?displayProperty=fullName> документации.

## <a name="reference"></a>Ссылка

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) предоставляет [редактор XML](http://go.microsoft.com/fwlink/?LinkId=228249) синтаксического анализа дерева через [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML-документов.

[Справочник по стандартам XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) содержит сведения о технологиях XML, включая XML, определение типа документа (DTD), язык определения схемы XML (XSD) и XSLT.

<xref:System.Xml?displayProperty=fullName> Описание классов и другие элементы, составляющие <xref:System.Xml> пространства имен и ссылки на более подробные сведения для каждого элемента.

<xref:System.Xml.Serialization?displayProperty=fullName> Описание классов и другие элементы, составляющие <xref:System.Xml.Serialization> пространства имен и ссылки на более подробные сведения о каждом элементе.

## <a name="related-sections"></a>Связанные разделы

[XML объекта модели (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom) описывает как <xref:System.Xml.XmlDocument> и связанные с ним классы соответствуют объектной модели документов W3C (Core) уровня 1 и спецификации пространству имен уровня 2.

[Обработка XML-данных с помощью XmlReader и XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[Преобразования XSLT](/dotnet/standard/data/xml/xslt-transformations) описывает как <xref:System.Xml.Xsl.XslCompiledTransform> класс реализует рекомендации XSLT 1.0.

[Обработка XML-данных с помощью модели данных XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) описывает как <xref:System.Xml.XPath.XPathNavigator> класс может обрабатывать XML-данные, хранящиеся в <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> объекта. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.

[Объектной модели схемы XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) описаны классы, используемые для создания и обработки XML-схем, предоставляя <xref:System.Xml.Schema.XmlSchema> класс для загрузки и изменения схемы.