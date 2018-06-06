---
title: Редактор XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2111286afde9e60391f1a7410fec2778b3ed673
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693790"
---
# <a name="xml-editor"></a>Редактор XML

Редактор XML основан на текстовом редакторе Visual Studio и включает дополнительную поддержку языков XML. XML editor включает следующие компоненты:

- Проверка синтаксиса XML 1.0.

- Проверка правильности по схеме во время ввода.

- Поддержка XML-фрагментов, включая фрагменты, сформированные схемой.

- Поддержка определения типа документа (DTD).

- Поддержка схем на языке XSD.

- Создание схемы XML из экземпляра XML-документа.

- Преобразование определения DTD или XDR-схемы в XML-схему.

- Проверка синтаксиса XSLT 1.0.

- Структурирование документов, позволяющее разворачивать и сворачивать элементы.

- Интеграция с [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md). Это обеспечивает иерархическое представление XML-схем.

Редактор XML вызывается для распространенных расширений файлов, таких как *.xml*, *.xsd*, *.xsl*, и *.config*. Также это приложение вызывается для неизвестных расширений имен файлов, если есть основания полагать, что файл содержит код XML. Также можно открыть любой файл в редакторе XML с помощью **открыть с помощью** параметр и выбрав редактор XML из списка.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) позволяет автоматически заполнять имена наборов атрибутов, режимы шаблонов и имена и имена параметров для указанного режима или именованного шаблона.

## <a name="xslt-profiler"></a>Профилировщик XSLT

[Профилировщик XSLT](../xml-tools/walkthrough-xslt-profiler.md) создает подробные производительности XSLT, отчетов, помогающих измерять, оценивать и устранять проблемы, связанные с производительностью в код XSLT. Профилировщик XSLT также содержит полезные подсказки по оптимизации таблиц стилей XSL и XSLT.

## <a name="xslt-hierarchy"></a>Иерархия XSLT

[Средство XSLT иерархии](../xml-tools/walkthrough-using-xslt-hierarchy.md) позволяет добавлять точки останова в включенные таблицы стилей и/или встроенные правила шаблона.

## <a name="see-also"></a>См. также

- [Компоненты редактора кода](../ide/writing-code-in-the-code-and-text-editor.md) предоставляет сведения о текстовом редакторе.
- [Справочник по стандартам XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) предоставляет сведения о технологиях XML, в том числе XML, определение типа документа (DTD), язык определения схем XML (XSD) и XSLT.
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)