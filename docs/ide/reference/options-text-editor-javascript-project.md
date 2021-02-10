---
title: "\"Параметры\", \"Текстовый редактор\", JavaScript, \"Проект\""
description: Сведения о том, как определить параметры проекта JavaScript и TypeScript в редакторе кода с помощью страницы "Проект" диалогового окна "Параметры".
ms.custom: SEO-VS-2020
ms.date: 06/19/2020
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b30aaec3087cece63e392cf7170ac85f6be0ad7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932336"
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

Эти параметры позволяют определить, будут ли файлы TypeScript, которые не являются частью проекта, компилироваться автоматически. Visual Studio выполняет сборку с использованием последней версии TypeScript, которая находится в папке *C:\Program Files (x86)\Microsoft SDKs\TypeScript*.

Установите флажок и выберите используемый тип создания кода.

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