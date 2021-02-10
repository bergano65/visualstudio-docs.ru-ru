---
title: Редактор XML
description: Узнайте о редакторе XML в Visual Studio, который построен на основе текстового редактора и включает дополнительную поддержку языков на базе XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de79063eeef5056bd850d8fa1fe76d6698c7e082
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874850"
---
# <a name="xml-editor"></a>Редактор XML

Редактор XML в Visual Studio построен на основе текстового редактора и включает дополнительную поддержку языков на базе XML. Если открыть XML-файл в Visual Studio, он откроется в редакторе XML.

Редактор XML включает следующие возможности.

- Проверка синтаксиса XML 1.0.

- Проверка правильности по схеме во время ввода.

- Поддержка XML-фрагментов, включая фрагменты, сформированные схемой.

- Поддержка определения типа документа (DTD).

- Поддержка схем на языке XSD.

- Создание схемы XML из экземпляра XML-документа.

- Преобразование определения DTD или XDR-схемы в XML-схему.

- Проверка синтаксиса XSLT.

- Структурирование документов, позволяющее разворачивать и сворачивать элементы.

- Интеграция с [обозревателем XML-схем](../xml-tools/xml-schema-explorer.md). Обеспечивает иерархическое представление XML-схем.

Редактор XML вызывается для распространенных расширений файлов, таких как *XML*, *XSD*, *XSL* и *CONFIG*. Также это приложение вызывается для неизвестных расширений имен файлов, если есть основания полагать, что файл содержит код XML.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

Функция [XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) позволяет автоматически заполнять имена наборов атрибутов; режимы шаблонов и имена; а также имена параметров для указанного режима или именованного шаблона.

## <a name="xslt-profiler"></a>Профилировщик XSLT

[Профилировщик XSLT](../xml-tools/xslt-profiler.md) создает подробные отчеты о производительности XSLT, помогающие измерять, оценивать и выявлять проблемы в XSLT-коде, связанные с производительностью. Профилировщик XSLT также содержит полезные подсказки по оптимизации таблиц стилей XSL и XSLT.

## <a name="xslt-hierarchy"></a>Иерархия XSLT

[Средство управления иерархией XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md) позволяет добавлять точки останова во включенные таблицы стилей и/или встроенные правила шаблона.

## <a name="see-also"></a>См. также

- [Параметры редактора XML — форматирование](../ide/reference/options-text-editor-xml-formatting.md)
- [Параметры редактора HTML — прочее](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [Возможности редактора кода](../ide/writing-code-in-the-code-and-text-editor.md)
- [Справочник по XML-стандартам](/previous-versions/dotnet/netframework-4.0/ms256177(v=vs.100))
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)