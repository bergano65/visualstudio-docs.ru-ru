---
title: Редактор XML и конструктор схем
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
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526572"
---
# <a name="xml-tools-in-visual-studio"></a>Средства XML в Visual Studio

*Расширяемый язык разметки (XML)* — это язык разметки, позволяющий описывать данные. XML отделяет данные и их представлением, с помощью связанных таблиц стилей например Extensible Stylesheet Language (XSL) и каскадных таблиц стилей (CSS). Visual Studio включает инструменты и возможности, облегчающие работу с XML, XSLT и XML-схемами.

## <a name="xml-editor"></a>Редактор XML

[Редактор XML](xml-editor.md) используется для редактирования XML-документов. Он предоставляет полный синтаксис XML, проверка, проверка схемы во время ввода, цветовое кодирование и IntelliSense. Если предоставлена схема или определение типа документа, технология IntelliSense выводит список разрешенных элементов и атрибутов.

Дополнительные возможности:

- Поддержка XML-фрагментов, включая фрагменты, сформированные схемой

- Структурирование документов, можно разворачивать и сворачивать элементы

- Возможность выполнять преобразования XSLT и просматривать результаты в виде текста, XML или HTML

- Возможность создания схем языка определения схемы XML из экземпляра XML-документа

- Поддержка редактирования таблиц стилей XSLT, включая поддержку технологии IntelliSense

- Обозреватель схемы XML

## <a name="xml-schema-designer"></a>Конструктор схемы XML

[Конструктор XML-схем](xml-schema-designer.md) интегрирован с Visual Studio и редактором XML, чтобы можно было работать со схемами языка определения схемы XML.

## <a name="xslt-debugging"></a>Отладка XSLT

Visual Studio поддерживает [отладка таблиц стилей XSLT](../xml-tools/debugging-xslt.md). С помощью отладчика можно задавать точки останова в таблице стилей XSLT, переходить в таблицу стилей XSLT из кода и т. д.

> [!NOTE]
> Отладчик XSLT доступен только в выпуске Visual Studio Enterprise.

## <a name="see-also"></a>См. также

- <xref:System.Xml?displayProperty=fullName>
- [Преобразования XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Обработка XML-данных с помощью модели данных XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Модель объектов документов XML (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Модель объектов схемы XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)