---
title: "\"Параметры\", \"Текстовый редактор\", \"Общие\" | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662260"
---
# <a name="options-text-editor-general"></a>Параметры, текстовый редактор, общие
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Это диалоговое окно позволяет изменять глобальные параметры для редактора кода и текста [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Для вывода этого диалогового окна щелкните элемент **Параметры** в меню **Сервис**, разверните папку **Текстовый редактор**, а затем щелкните **Общие**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Параметры
 Перетаскивание редактирования текста при выборе позволяет перемещать текст, выбирая его и перетаскивая мышью в другое место в текущем документе или в любой другой открытый документ.

 Автоматическое выделение разделителей. Если выбрано, выделяются символы-разделители, разделяющие параметры или пары "элемент-значение", а также Парные фигурные скобки.

 Отслеживание изменений при выборе редактора кода в поле выбора появляется вертикальная желтая линия, помечающая код, который был изменен с момента последнего сохранения файла. При сохранении изменений вертикальные линии становятся зелеными.

 Автоматически определять кодировку UTF-8 без сигнатуры по умолчанию редактор определяет кодировку, выполняя поиск меток порядка байтов или тегов charset. Если их не удается найти в текущем документе, редактор кода пытается автоматически определить кодировку UTF-8 путем сканирования последовательностей байтов. Чтобы отключить автоматическое определение кодировки, снимите этот флажок.

## <a name="display"></a>Отображение
 Поле выделения. отображает вертикальное поле вдоль левого края текстового поля редактора. Можно щелкнуть это поле, чтобы выделить всю строку текста, или щелкнуть и перетащить последовательные строки текста.

|Поле выделения включено|Поле выделения выключено|
|-------------------------|--------------------------|
|![Снимок экрана HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "вксселмарон")|![Снимок экрана HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "вксселмарофф")|

 Поле индикатора Если выбрано, отображается вертикальное поле за пределами левого края текстового поля редактора. Если щелкнуть это поле, отображаются значок и подсказка, связанные с текстом. Например, в поле индикаторов отображаются ярлыки точки останова или списка задач. Сведения в поле индикаторов не выводятся на печать.

 Вертикальная полоса прокрутки Если выбрана, отображается вертикальная полосы прокрутки, которая позволяет прокручивать вверх и вниз для просмотра элементов, находящихся за пределами области просмотра редактора. Если вертикальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши PAGE UP, PAGE DOWN и клавиши управления курсором.

 Горизонтальная полоса прокрутки Если выбрана, отображает горизонтальную полосу прокрутки, которая позволяет выполнять прокрутку от стороны к элементам для просмотра элементов, находящихся за пределами области просмотра редактора. Если горизонтальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши управления курсором.

 Выделение текущей строки если выбрано, отображает серое поле вокруг строки кода, в которой находится курсор.

## <a name="see-also"></a>См. также:
 [Параметры, текстовый редактор, все языки,](../../ide/reference/options-text-editor-all-languages.md) [текстовый редактор, все языки, параметры табуляции](../../ide/reference/options-text-editor-all-languages-tabs.md) [, текстовый редактор, расширение файла](../../ide/reference/options-text-editor-file-extension.md) [Определение и настройка сочетаний клавиш](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [Настройка редактора](../../ide/customizing-the-editor.md) [с помощью IntelliSense](../../ide/using-intellisense.md)
