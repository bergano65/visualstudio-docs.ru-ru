---
title: Средства XML в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: bcc9a3d40aec66eb63543e1e038027b588e61889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560022"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [средства XML в Visual Studio](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio).  
  
  
Расширяемый язык разметки (XML) * — это язык разметки, позволяющий описывать данные. Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах. Кроме того, XML позволяет разделять представление от данных. Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления. В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей (CSS). XML отделяет данные от представления и обработки. Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.  
  
 XML — это подмножество языка SGML, оптимизированное для доставки через Интернет. Его спецификация определяется консорциумом World Wide Web (W3C). Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.  
  
 XML лежит в основе многих возможностей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. В следующем разделе перечислены средства и возможности, связанныe с XML, которые доступны в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Дополнительные сведения см. в разделе [Центр разработчиков XML](http://go.microsoft.com/fwlink/?LinkID=100176), который предоставляет последнюю документацию, технические сведения, файлы для загрузки, группы новостей и другие ресурсы для разработчиков XML.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md)  
 Описание роли XML в обработке данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)  
 Ссылки на разделы об использовании отладчика Visual для отладки XSLT.  
  
## <a name="reference"></a>Ссылка  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Предоставляет [редактор XML](http://go.microsoft.com/fwlink/?LinkId=228249) синтаксического анализа дерева через [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML-документов.  
  
 [Справочник по XML-стандартам](http://msdn.microsoft.com/en-us/79c78508-c9d0-423a-a00f-672e855de401)  
 Сведения о технологиях XML, в том числе XML, определении типа документа (DTD), языке определения схемы XML (XSD) и XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml>, а также ссылки на более подробное описание каждого элемента.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml.Serialization>, а также ссылки на более подробное описание каждого элемента.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Модель объектов документов XML (DOM)](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54)  
 Описание соответствия <xref:System.Xml.XmlDocument> и связанных классов спецификации пространству имен объектной модели документов W3C (базовой) уровня 1 и 2.  
  
 [Чтение XML с помощью XmlReader](http://msdn.microsoft.com/en-us/3029834c-a27e-4331-b7aa-711924062182)  
 Описание предоставления однонаправленного доступа только для чтения без кэша к данным XML по потоку XML с помощью <xref:System.Xml.XmlReader>.  
  
 [Запись XML с помощью XmlWriter](http://msdn.microsoft.com/en-us/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Описание того, как <xref:System.Xml.XmlWriter> позволяет создавать XML-потоки без кэша и помогает создавать XML-документы, соответствующие стандарту W3C.  
  
 [Преобразования XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)  
 Описание реализации рекомендации XSLT 1.0 в классе <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Обработка XML-данных с использованием модели данных XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)  
 Описание того, как класс <xref:System.Xml.XPath.XPathNavigator> может обрабатывать данные XML, которые хранятся в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>. Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.  
  
 [Модель объектов схемы XML (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd)  
 Описание классов, используемых для создания и обработки схем XML с применением класса <xref:System.Xml.Schema.XmlSchema> для загрузки и редактирования схемы.



