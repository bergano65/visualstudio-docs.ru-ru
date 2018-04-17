---
title: Средства XML в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f823a42d5a89dd22fd273a2971a3b323487a525b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio

*Расширяемый язык разметки (XML)* — это язык разметки, позволяющий описывать данные. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей (CSS). XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.

XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.

XML лежит в основе многих возможностей Visual Studio и .NET Framework. В следующем разделе перечислены средства и функции, относящиеся к XML, которые предлагаются в Visual Studio и .NET Framework.

Дополнительные сведения см. в разделе <xref:System.Xml?displayProperty=fullName> документации.

## <a name="in-this-section"></a>В этом разделе

[Работа с XML-данными](../xml-tools/working-with-xml-data.md)  
Описание роли XML в методе обработки данных в Visual Studio.

[Отладка XSLT](../xml-tools/debugging-xslt.md)  
Ссылки на разделы об использовании отладчика Visual для отладки XSLT.

## <a name="reference"></a>Ссылка

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
Предоставляет [редактора XML](http://go.microsoft.com/fwlink/?LinkId=228249) синтаксический анализ дерева с помощью [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML-документов.

[Справочник по XML-стандартам](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)  
Сведения о технологиях XML, в том числе XML, определении типа документа (DTD), языке определения схемы XML (XSD) и XSLT.

<xref:System.Xml?displayProperty=fullName>  
Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml>, а также ссылки на более подробное описание каждого элемента.

<xref:System.Xml.Serialization?displayProperty=fullName>  
Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml.Serialization>, а также ссылки на более подробное описание каждого элемента.

## <a name="related-sections"></a>Связанные разделы

[Модель объектов документов XML (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
Описание соответствия <xref:System.Xml.XmlDocument> и связанных классов спецификации пространству имен объектной модели документов W3C (базовой) уровня 1 и 2.

[Обработка XML-данных с XmlReader и XmlWriter](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[Преобразования XSLT](/dotnet/standard/data/xml/xslt-transformations)  
Описание реализации рекомендации XSLT 1.0 в классе <xref:System.Xml.Xsl.XslCompiledTransform>.

[Обработка XML-данных с использованием модели данных XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
Описание того, как класс <xref:System.Xml.XPath.XPathNavigator> может обрабатывать данные XML, которые хранятся в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.

[Модель объектов схемы XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)  
Описание классов, используемых для создания и обработки схем XML с применением класса <xref:System.Xml.Schema.XmlSchema> для загрузки и редактирования схемы.