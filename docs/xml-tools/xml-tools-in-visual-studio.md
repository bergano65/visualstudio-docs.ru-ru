---
title: Конструктор схем и редактор XML
description: Узнайте о средствах Visual Studio для работы со схемами XML, XSLT и XML, включая редактор XML, конструктор XML-схем и отладчик XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
- XML [Visual Studio], .NET classes
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3e376980fb7c1e7f2378f23ae8230e6e45264ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874773"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Обзор средств XML в Visual Studio

*XML* — это язык разметки, предоставляющий формат для описания данных. XML разделяет данные и их представление, используя связанные таблицы стилей, такие как XSL и CSS. Visual Studio включает инструменты и возможности, облегчающие работу с XML, XSLT и XML-схемами.

## <a name="xml-editor"></a>Редактор XML

[Редактор XML](xml-editor.md) используется для редактирования XML-документов. Он предлагает полную проверку синтаксиса XML, проверку схемы по мере ввода, цветовое кодирование и технологию IntelliSense. Если предоставлена схема или определение типа документа, технология IntelliSense выводит список разрешенных элементов и атрибутов.

Дополнительные возможности:

- Поддержка фрагментов XML, включая фрагменты, созданные схемой.

- Структурирование документов для разворачивания и сворачивания элементов.

- Возможность выполнять преобразования XSLT и просматривать результаты в виде текста, XML или HTML.

- Возможность создавать схемы на языке XSD из экземпляров документов XML.

- Поддержка редактирования таблиц стилей XSLT, включая поддержку технологии IntelliSense.

- Обозреватель схемы XML

## <a name="xml-schema-designer"></a>Конструктор схемы XML

[Конструктор схем XML](xml-schema-designer.md) интегрирован с Visual Studio 2010, а редактор XML позволяет работать со схемами XSD.

## <a name="xslt-debugging"></a>Отладка XSLT

Visual Studio поддерживает [отладку таблиц стилей XSLT](../xml-tools/debugging-xslt.md). С помощью отладчика можно задавать точки останова в таблице стилей XSLT, переходить в таблицу стилей XSLT из кода и т. д.

> [!NOTE]
> Отладчик XSLT предоставляется только в выпуске Visual Studio 2017 Enterprise.

## <a name="see-also"></a>См. также

- <xref:System.Xml?displayProperty=fullName>
- [Преобразования XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Обработка данных XML с использованием модели данных XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Модель объектов документов XML (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Модель объектов схемы XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)
