---
title: Средства XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 313cc11978355942bf6671cc040969c255d7e44d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669347"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Язык XML (XML) * — это язык разметки, который предоставляет формат для описания данных. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей (CSS). XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.

 XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.

 XML лежит в основе многих возможностей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. В следующем разделе перечислены средства и возможности, связанныe с XML, которые доступны в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Дополнительные сведения см. в [центре разработчиков XML](http://go.microsoft.com/fwlink/?LinkID=100176), который содержит последнюю документацию, технические сведения, файлы для загрузки, группы новостей и другие ресурсы для разработчиков XML.

## <a name="in-this-section"></a>Содержание
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md) Обсуждается роль XML в способе обработки данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Отладка XSLT](../xml-tools/debugging-xslt.md) Содержит ссылки на разделы, посвященные использованию отладчика Visual Studio для отладки XSLT.

## <a name="reference"></a>Справочник
 [Microsoft. VisualStudio. XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) предоставляет дерево синтаксического анализа [XML-редактора](http://go.microsoft.com/fwlink/?LinkId=228249) через [System. XML. LINQ](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML-документов.

 [Справочник по стандартам XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Предоставляет сведения о технологиях XML, включая XML, определение типа документа (DTD), язык определения схемы XML (XSD) и XSLT.

 <xref:System.Xml?displayProperty=fullName> описывает классы и другие элементы, составляющие пространство имен <xref:System.Xml>, и ссылки на более подробные сведения о каждом элементе.

 <xref:System.Xml.Serialization?displayProperty=fullName> описываются классы и другие элементы, составляющие пространство имен <xref:System.Xml.Serialization>, а также ссылки на более подробные сведения о каждом элементе.

## <a name="related-sections"></a>Связанные разделы
 [Модель DOM XML (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Описывает, как <xref:System.Xml.XmlDocument> и связанные с ними классы соответствуют спецификациям поддержки пространств имен модель DOM уровня 1 и уровня 2 консорциума W3C.

 [Считывание XML с помощью XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Описывает, как <xref:System.Xml.XmlReader> предоставляет доступ только для чтения к XML-данным в потоке XML с некэшированным прямым доступом.

 [Запись XML с помощью XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Описывает, как <xref:System.Xml.XmlWriter> предоставляет некэшированный, перенаправленный только способ создания XML-потоков и помогает создавать XML-документы, соответствующие стандарту W3C.

 [Преобразования XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Описывает, как класс <xref:System.Xml.Xsl.XslCompiledTransform> реализует рекомендацию XSLT 1,0.

 [Обработка XML-данных с помощью модели данных XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Описывает, как класс <xref:System.Xml.XPath.XPathNavigator> может обрабатывать XML-данные, хранящиеся в <xref:System.Xml.XPath.XPathDocument> или в объекте <xref:System.Xml.XmlDocument>. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.

 [Модель объектов схемы XML (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Описывает классы, используемые для создания схем XML и управления ими, предоставляя класс <xref:System.Xml.Schema.XmlSchema> для загрузки и редактирования схемы.
