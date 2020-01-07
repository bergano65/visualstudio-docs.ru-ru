---
title: Редактор XML
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10741daffff2213e8ababde2395663e78241fdc4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592403"
---
# <a name="xml-editor"></a>Редактор XML

Редактор XML в Visual Studio основан на текстовом редакторе и включает дополнительную поддержку для языков XML. При открытии XML-файла в Visual Studio он открывается в редакторе XML.

Редактор XML включает следующие функции:

- Проверка синтаксиса XML 1.0.

- Проверка правильности по схеме во время ввода.

- Поддержка XML-фрагментов, включая фрагменты, сформированные схемой.

- Поддержка определения типа документа (DTD).

- Поддержка схем на языке XSD.

- Создание схемы XML из экземпляра XML-документа.

- Преобразование определения DTD или XDR-схемы в XML-схему.

- Проверка синтаксиса XSLT.

- Структурирование документов, позволяющее разворачивать и сворачивать элементы.

- Интеграция с [обозревателем XML-схем](../xml-tools/xml-schema-explorer.md). Это обеспечивает иерархическое представление XML-схем.

Редактор XML вызывается для хорошо известных расширений файлов, таких как *. XML*, *. xsd*, *. xsl*и *. config*. Он также вызывается для любого неизвестного расширения файла, если файл содержит XML.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[Технология XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) позволяет автозаполнению имен наборов атрибутов, режимов шаблонов и имен параметров для указанного режима или указанного именованного шаблона.

## <a name="xslt-profiler"></a>Профилировщик XSLT

[Профилировщик XSLT](../xml-tools/xslt-profiler.md) создает подробные отчеты о производительности XSLT, которые помогают измерять, оценивать и нацелить проблемы, связанные с производительностью, в коде XSLT. Профилировщик XSLT также содержит полезные подсказки по оптимизации таблиц стилей XSL и XSLT.

## <a name="xslt-hierarchy"></a>Иерархия XSLT

С помощью [инструмента "XSLT-иерархия](../xml-tools/walkthrough-using-xslt-hierarchy.md) " можно добавлять точки останова в встроенные таблицы стилей или правила шаблонов.

## <a name="see-also"></a>См. также:

- [Параметры редактора XML — форматирование](../ide/reference/options-text-editor-xml-formatting.md)
- [Параметры редактора XML — Разное](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [Возможности редактора кода](../ide/writing-code-in-the-code-and-text-editor.md)
- [Справочник по стандартам XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
