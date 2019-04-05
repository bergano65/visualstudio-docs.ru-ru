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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2812e45460778a3527f55522c6d3fc98285a548d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992151"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Расширяемый язык разметки (XML) * — это язык разметки, позволяющий описывать данные. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей (CSS). XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.

 XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.

 XML лежит в основе многих возможностей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. В следующем разделе перечислены средства и возможности, связанныe с XML, которые доступны в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Дополнительные сведения см. в разделе [Центр разработчиков XML](http://go.microsoft.com/fwlink/?LinkID=100176), который предоставляет последнюю документацию, технические сведения, файлы для загрузки, группы новостей и другие ресурсы для разработчиков XML.

## <a name="in-this-section"></a>В этом разделе
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md) описание роли XML в данных обрабатывается в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Отладка XSLT](../xml-tools/debugging-xslt.md) ссылки на разделы об использовании отладчика Visual Studio для отладки XSLT.

## <a name="reference"></a>Ссылка
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) предоставляет [редактор XML](http://go.microsoft.com/fwlink/?LinkId=228249) синтаксического анализа дерева через [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML-документов.

 [Справочник по стандартам XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) содержит сведения о технологиях XML, включая XML, определение типа документа (DTD), язык определения схемы XML (XSD) и XSLT.

 <xref:System.Xml?displayProperty=fullName> Описание классов и другие элементы, составляющие <xref:System.Xml> пространства имен и ссылки на более подробные сведения для каждого элемента.

 <xref:System.Xml.Serialization?displayProperty=fullName> Описание классов и другие элементы, составляющие <xref:System.Xml.Serialization> пространства имен и ссылки на более подробные сведения о каждом элементе.

## <a name="related-sections"></a>Связанные разделы
 [XML объекта модели (DOM)](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) описывает как <xref:System.Xml.XmlDocument> и связанные с ним классы соответствуют объектной модели документов W3C (Core) уровня 1 и спецификации пространству имен уровня 2.

 [Чтение XML с XmlReader](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) описывает как <xref:System.Xml.XmlReader> предоставляет однонаправленное только для чтения к данным XML в XML-потоке.

 [Запись XML-кода с помощью XmlWriter](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) описывает как <xref:System.Xml.XmlWriter> Однонаправленная пересылать только способ формирования XML-потоки и помогает создавать XML-документов, соответствующих стандарту W3C.

 [Преобразования XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) описывает как <xref:System.Xml.Xsl.XslCompiledTransform> класс реализует рекомендации XSLT 1.0.

 [Обработка XML-данных с помощью модели данных XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) описывает как <xref:System.Xml.XPath.XPathNavigator> класс может обрабатывать XML-данные, хранящиеся в <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> объекта. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.

 [Объектной модели схемы XML (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) описаны классы, используемые для создания и обработки XML-схем, предоставляя <xref:System.Xml.Schema.XmlSchema> класс для загрузки и изменения схемы.
