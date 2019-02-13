---
title: "\"Параметры\", \"Текстовый редактор\", \"Все языки\", \"Вкладки\""
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09bf4f205b7fc200038b2aedfcf3a8318cb1c7a9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954872"
---
# <a name="options-text-editor-all-languages-tabs"></a>"Параметры", "Текстовый редактор", "Все языки", "Вкладки"

Это диалоговое окно позволяет изменять стандартное поведение редактора кода. Эти параметры также применяются к другим редакторам, основанным на редакторе кода, таким как представление исходного кода в конструкторе HTML. Чтобы отобразить эти параметры, выберите в меню **Сервис** пункт **Параметры**. В папке **Текстовый редактор** разверните подпапку **Все языки**, а затем выберите **Табуляция**.

> [!CAUTION]
> На этой странице задаются параметры по умолчанию для всех языков разработки. Не забывайте, что сброс параметра в этом диалоговом окне приведет к возврату параметров табуляции для всех языков к выбранному здесь значению. Чтобы изменить параметры текстового редактора только для одного языка, раскройте подпапку для этого языка и выберите соответствующие страницы параметров.

Если для конкретных языков программирования на страницах параметров табуляции выбраны разные параметры, то для разных параметров **отступов** отображается сообщение "Параметры отступов для разных текстовых форматов конфликтуют друг с другом", а для разных параметров **табуляции** — сообщение "Параметры табуляции для разных текстовых форматов конфликтуют друг с другом". Например, это напоминание выводится, если для Visual Basic задан параметр **Интеллектуальные отступы**, а для Visual C++ — параметр **Отступ блока**.

## <a name="indenting"></a>Отступы

Нет

Если выбран этот параметр, новые строки не отображаются с отступом. Точка вставки помещается в первый столбец новой строки.

Block

Если выбран этот параметр, для новых строк отступ задается автоматически. Точка вставки помещается в той же начальной точке, что и в предыдущей строке.

Структура

Если выбран этот параметр, новые строки располагаются по размеру контекста кода, в соответствии с другими параметрами форматирования кода и соглашениями IntelliSense для выбранного языка разработки. Этот параметр доступен не для всех языков разработки.

Например, строки, заключенные между открывающей фигурной скобкой "( { )" и закрывающей фигурной скобкой "( } )", автоматически получают отступ на дополнительную табуляцию с позиции выравнивания фигурных скобок.

## <a name="tabs"></a>Вкладки

Размер шага табуляции

Устанавливает расстояние между позициями табуляции в пробелах. По умолчанию — четыре пробела.

Размер отступа

Задает размер автоматического отступа в пробелах. По умолчанию — четыре пробела. Для заполнения указанного размера будут вставлены знаки табуляции, пробелы или и те и другие.

Вставить пробелы

Когда выбран этот параметр, при отступе вставляются только пробелы, а не символы табуляции. Например, если **Размер отступа** равен 5, то при каждом нажатии клавиши TAB или кнопки **Увеличить отступ** на панели инструментов **Форматирование** будет вставляться пять пробелов.

Сохранять символы табуляции

Если выбран этот параметр, при отступе вставляется максимально возможное число знаков табуляции. Символ табуляции вставляет такое число пробелов, которое указано в поле **Размер интервала табуляции**. Если **размер отступа** не кратен **размеру интервала табуляции**, для заполнения разницы добавляются знаки пробелов.

## <a name="see-also"></a>См. также

- ["Параметры", "Текстовый редактор", "Все языки"](../../ide/reference/options-text-editor-all-languages.md)
- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)