---
title: "\"Параметры\", \"Текстовый редактор\", JavaScript, \"Анализ кода\""
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c62970ab6377ddaaf295007fd49ba8be7dd225
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026286"
---
# <a name="options-text-editor-javascript-linting"></a>"Параметры", "Текстовый редактор", JavaScript, "Анализ кода"

Страница **Анализ кода** диалогового окна **Параметры** позволяет задавать параметры анализа кода в редакторе кода. Чтобы открыть эту страницу, выберите в строке меню **Сервис** > **Параметры**, затем разверните **Текстовый редактор** > **JavaScript** > **Анализ кода**.

## <a name="eslint-settings"></a>Параметры ESLint

Эти параметры позволяют включить статический анализ кода JavaScript и выбрать файлы для анализа. Дополнительные сведения об ESLint см. на веб-сайте [ESLint.org](https://eslint.org/).

### <a name="uielement-list"></a>Список элементов пользовательского интерфейса

|Параметр|Описание|
|------------|-----------------|
|**Включить ESLint**|Если выбран этот параметр, в редакторе кода можно выполнять статический анализ кода.|
|**Lint all files included in project, even closed files** (Проанализировать все файлы, включенные в проект, даже закрытые)|Если этот параметр выбран, анализируются закрытые файлы, если не предусмотрена диагностика только открытых файлов.|

## <a name="global-eslint-config-options"></a>Global ESLint Config Options (Параметры глобальной конфигурации ESLint)

Этот параметр позволяет скопировать расположение файла глобальной конфигурации ESLint. Кроме того, если ранее вы меняли расположение файла, можно восстановить его расположение по умолчанию.

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)