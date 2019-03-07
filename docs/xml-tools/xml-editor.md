---
title: Редактор XML
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39e069dfd65294ed3d40342816e871757378a57b
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526195"
---
# <a name="xml-editor"></a>Редактор XML

Редактор XML в Visual Studio основана на текстовом редакторе и включает дополнительную поддержку языков XML. При открытии файла XML в Visual Studio, он открывается в редакторе XML.

Редактор XML включает в себя следующие компоненты:

- Проверка синтаксиса XML 1.0.

- Проверка правильности по схеме во время ввода.

- Поддержка XML-фрагментов, включая фрагменты, сформированные схемой.

- Поддержка определения типа документа (DTD).

- Поддержка схем на языке XSD.

- Создание схемы XML из экземпляра XML-документа.

- Преобразование определения DTD или XDR-схемы в XML-схему.

- Проверка синтаксиса XSLT.

- Структурирование документов, позволяющее разворачивать и сворачивать элементы.

- Интеграция с [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md). Это обеспечивает иерархическое представление XML-схем.

Редактор XML вызывается для распространенных расширений файлов, таких как *.xml*, *.xsd*, *.xsl*, и *.config*. Также это приложение вызывается для неизвестных расширений имен файлов, если есть основания полагать, что файл содержит код XML.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) позволяет автоматически заполнять имена наборов атрибутов, режимы шаблонов и имена или имена параметров для указанного режима или именованного шаблона.

## <a name="xslt-profiler"></a>Профилировщик XSLT

[Профилировщик XSLT](../xml-tools/xslt-profiler.md) создает подробные сведения о производительности XSLT, отчеты, которые помогают измерять, оценивать и исправлять проблемы, связанные с производительностью, в код XSLT. Профилировщик XSLT также содержит полезные подсказки по оптимизации таблиц стилей XSL и XSLT.

## <a name="xslt-hierarchy"></a>XSLT иерархии

[Средство XSLT иерархии](../xml-tools/walkthrough-using-xslt-hierarchy.md) позволяет добавлять точки останова в включаемая таблицы стилей и/или встроенные правила шаблона.

## <a name="see-also"></a>См. также

- [Параметры редактора XML - форматирование](../ide/reference/options-text-editor-xml-formatting.md)
- [Параметры редактора XML - Разное](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [Возможности редактора кода](../ide/writing-code-in-the-code-and-text-editor.md)
- [Справочник по стандартам XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)