---
title: "Средства XML в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "классы [Visual Studio], XML"
  - "CSS, таблицы стилей для XML"
  - "данные [Visual Studio], XML"
  - "наборы данных [Visual Basic], схемы XML"
  - "файлы обнаружения, XML"
  - "Шаблоны предприятия, XML и"
  - "серверные элементы управления, XML и"
  - "SGML, XML"
  - "таблицы стилей, для XML"
  - "серверные веб-элементы управления, XML"
  - "веб-службы"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], с классами .NET Framework"
  - "XML [Visual Studio], источники данных"
  - "XML [Visual Studio], ресурсы"
  - "XML [Visual Studio], связь SGML"
  - "схемы XML"
  - "XMLDataDocument - класс"
  - "схемы XSD"
  - "XSL"
  - "XSL, таблицы стилей"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Средства XML в Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML* — это язык разметки, позволяющий описывать данные.  Он упрощает точное объявление контента и помогает получать более значимые результаты поиска на различных платформах.  Кроме того, XML позволяет разделять представление от данных.  Например, в HTML теги используются, чтобы сообщить браузеру, что данные должны быть выделены полужирным шрифтом или курсивом. В XML теги применяются только для описания данных, например названия города, температуры и атмосферного давления.  В XML для представления данных в браузере используются таблицы стилей, например таблицы XSL и каскадные таблицы стилей \(CSS\).  XML отделяет данные от представления и обработки.  Это позволяет отображать и обрабатывать данные необходимым способом, применяя различные таблицы стилей и приложения.  
  
 XML — это подмножество языка SGML, оптимизированное для доставки через Интернет.  Его спецификация определяется консорциумом World Wide Web \(W3C\).  Такая стандартизация гарантирует, что структурированные данные будут согласованными и независимыми от приложений или поставщиков.  
  
 XML лежит в основе многих возможностей [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  В следующем разделе перечислены средства и возможности, связанныe с XML, которые доступны в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Дополнительные сведения см. в [Центре разработчиков XML](http://go.microsoft.com/fwlink/?LinkID=100176), где представлены последняя документация, техническая информация, файлы для загрузки, новостные группы и другие ресурсы для разработчиков XML.  
  
## В этом подразделе  
 [Работа с XML\-данными](../xml-tools/working-with-xml-data.md)  
 Описание роли XML в обработке данных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)  
 Ссылки на разделы об использовании отладчика Visual для отладки XSLT.  
  
## Ссылка  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Предоставляет доступ к дереву синтаксического анализа [редактора XML](http://go.microsoft.com/fwlink/?LinkId=228249) через [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) для любых XML\-документов.  
  
 [Справочник по XML\-стандартам](http://msdn.microsoft.com/ru-ru/79c78508-c9d0-423a-a00f-672e855de401)  
 Сведения о технологиях XML, в том числе XML, определении типа документа \(DTD\), языке определения схемы XML \(XSD\) и XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml>, а также ссылки на более подробное описание каждого элемента.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Описание классов и других элементов, из которых состоит пространство имен <xref:System.Xml.Serialization>, а также ссылки на более подробное описание каждого элемента.  
  
## Связанные подразделы  
 [Модель DOM для XML](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Описание соответствия <xref:System.Xml.XmlDocument> и связанных классов спецификации пространству имен объектной модели документов W3C \(базовой\) уровня 1 и 2.  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/ru-ru/3029834c-a27e-4331-b7aa-711924062182)  
 Описание предоставления однонаправленного доступа только для чтения без кэша к данным XML по потоку XML с помощью <xref:System.Xml.XmlReader>.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/ru-ru/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Описание того, как <xref:System.Xml.XmlWriter> позволяет создавать XML\-потоки без кэша и помогает создавать XML\-документы, соответствующие стандарту W3C.  
  
 [Преобразования XSLT](../Topic/XSLT%20Transformations.md)  
 Описание реализации рекомендации XSLT 1.0 в классе <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Обработка XML\-данных с использованием модели данных XPath](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Описание того, как класс <xref:System.Xml.XPath.XPathNavigator> может обрабатывать данные XML, которые хранятся в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>.  Класс <xref:System.Xml.XPath.XPathNavigator> основан на XQuery 1.0 и модели данных XPath 2.0 и может использоваться для просмотра и редактирования данных XML.  
  
 [Модель объектов схемы XML \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Описание классов, используемых для создания и обработки схем XML с применением класса <xref:System.Xml.Schema.XmlSchema> для загрузки и редактирования схемы.