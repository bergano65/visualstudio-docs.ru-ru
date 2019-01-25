---
title: "\"Параметры\", \"Текстовый редактор\", JavaScript, \"Проект\""
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7be14c9953fed34e7bdd9507b6224875b1008a22
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350298"
---
# <a name="options-text-editor-javascript-project"></a>"Параметры", "Текстовый редактор", JavaScript, "Проект"

В диалоговом окне **Параметры** перейдите на страницу **Проект**, чтобы определить параметры проекта JavaScript в редакторе кода. Чтобы открыть эту страницу, выберите в строке меню **Инструменты** > **Параметры** и перейдите к разделу **Текстовый редактор** > **JavaScript** > **Проект**.

## <a name="project-analysis-options"></a>Параметры анализа проекта

Эти параметры позволяют определить, как редактор будет анализировать проекты, отчеты о диагностике и предлагать улучшения. Установите или снимите флажки параметров, чтобы указать, как редактор должен обрабатывать эти файлы.

### <a name="uielement-list"></a>Список элементов пользовательского интерфейса

- **Анализировать только те проекты, которые содержат файлы, открытые в редакторе**
- **Диагностика выводится только для файлов, открытых в редакторе**
- **Предложить возможные улучшения, которые не являются исправлениями**

## <a name="virtual-projects-in-solution-explorer"></a>Виртуальные проекты в обозревателе решений

Эти параметры позволяют выбрать, когда отображать виртуальные проекты — если решение было загружено или не загружено. 

## <a name="compile-on-save"></a>Компилирование при сохранении

Эти параметры позволяют определить, будут ли файлы TypeScript, которые не являются частью проекта, компилироваться автоматически. Установите флажок и выберите используемый тип создания кода.

### <a name="uielement-list"></a>Список элементов пользовательского интерфейса

- **Использовать создание кода AMD для модулей, которые не являются частью проекта**
- **Использовать создание кода CommonJS для модулей, которые не являются частью проекта**
- **Use UMD code generation for modules that are not part of a project** (Использовать создание кода UMD для модулей, которые не являются частью проекта)
- **Use System code generation for modules that are not part of a project** (Использовать создание кода System для модулей, которые не являются частью проекта)
- **Use ES2015 code generation for modules that are not part of a project** (Использовать создание кода ES2015 для модулей, которые не являются частью проекта)

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Версия ECMAScript для файлов, которые не являются частью проекта

Эти параметры позволяют выбрать версию ECMAScript для файлов, которые не являются частью проекта. Вы можете выбрать следующие версии: **ECMAScript 3**, **ECMAScript 5** или **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Вывод JSX для TSX-файлов, которые не являются частью проекта

Эти параметры позволяют определить, как редактор будет обрабатывать файлы TypeScript, которые не являются частью проекта.

### <a name="uielement-list"></a>Список элементов пользовательского интерфейса

|Параметр|Описание|
|------------|-----------------|
|**Платформа React**|Если выбран этот параметр, текстовый редактор добавляет файлу расширение *.js*.|
|**Preserve**|Если выбран этот параметр, текстовый редактор сохраняет JSX как часть выходных данных и добавляет файлу расширение *.jsx*.|

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)