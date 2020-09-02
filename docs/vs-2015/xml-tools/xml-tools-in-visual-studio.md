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
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845973"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Язык XML (XML) * — это язык разметки, который предоставляет формат для описания данных. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей (CSS). XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.

 XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.

 XML лежит в основе многих возможностей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. В следующем разделе перечислены средства и возможности, связанныe с XML, которые доступны в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Дополнительные сведения см. в [центре разработчиков XML](https://msdn.microsoft.com/data/bb190600.aspx), который содержит последнюю документацию, технические сведения, файлы для загрузки, группы новостей и другие ресурсы для разработчиков XML.

## <a name="in-this-section"></a>в этом разделе
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md) Обсуждается роль XML в способе обработки данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [Отладка XSLT](../xml-tools/debugging-xslt.md) Содержит ссылки на разделы, посвященные использованию отладчика Visual Studio для отладки XSLT.

## <a name="reference"></a>Справочник
 [ РедакторMicrosoft.VisualStudio.Xml](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) Предоставляет дерево синтаксического анализа [XML-редактора](https://msdn.microsoft.com/library/ms255810.aspx) с помощью [System.Xml. LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) для любых XML-документов.

 [Справочник по стандартам XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Предоставляет сведения о технологиях XML, включая XML, определение типа документа (DTD), язык определения схемы XML (XSD) и XSLT.

 <xref:System.Xml?displayProperty=fullName> Описывает классы и другие элементы, составляющие <xref:System.Xml> пространство имен, и ссылки на более подробные сведения о каждом элементе.

 <xref:System.Xml.Serialization?displayProperty=fullName> Описывает классы и другие элементы, составляющие <xref:System.Xml.Serialization> пространство имен, а также ссылки на более подробные сведения о каждом элементе.

## <a name="related-sections"></a>См. также
 [Модель DOM XML (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Описание того, что <xref:System.Xml.XmlDocument> и связанные с ним классы соответствуют спецификациям поддержки пространств имен уровня 1 W3C модель DOM (Core) и уровня 2.

 [Считывание XML с помощью XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Описывает, как <xref:System.Xml.XmlReader> предоставляет доступ только для чтения к XML-данным через поток XML.

 [Запись XML с помощью XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Описывает, как <xref:System.Xml.XmlWriter> предоставляет возможность создания XML-документов без кэширования и пересылки, а также помогает создавать XML-документы, соответствующие стандарту W3C.

 [Преобразования XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Описывает, как <xref:System.Xml.Xsl.XslCompiledTransform> класс реализует рекомендацию XSLT 1,0.

 [Обработка XML-данных с помощью модели данных XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Описывает, как <xref:System.Xml.XPath.XPathNavigator> класс может обрабатывать XML-данные, хранящиеся в <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> объекте или. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.

 [Модель объектов схемы XML (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Описывает классы, используемые для создания схем XML и управления ими, предоставляя <xref:System.Xml.Schema.XmlSchema> класс для загрузки и редактирования схемы.
