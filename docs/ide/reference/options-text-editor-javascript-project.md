---
title: "\"Параметры\", \"Текстовый редактор\", JavaScript, \"Проект\""
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605928"
---
# <a name="options-text-editor-javascript-project"></a>"Параметры", "Текстовый редактор", JavaScript, "Проект"

В диалоговом окне **Параметры** перейдите на страницу **Проект**, чтобы определить параметры проекта JavaScript и TypeScript в редакторе кода. Чтобы открыть эту страницу, выберите в строке меню **Сервис** > **Параметры**, затем разверните **Текстовый редактор** > **JavaScript/TypeScript** > **Проект**.

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

|Параметр|ОПИСАНИЕ|
|------------|-----------------|
|**Платформа React**|Если выбран этот параметр, текстовый редактор добавляет файлу расширение *.js*.|
|**Preserve**|Если выбран этот параметр, текстовый редактор сохраняет JSX как часть выходных данных и добавляет файлу расширение *.jsx*.|

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)