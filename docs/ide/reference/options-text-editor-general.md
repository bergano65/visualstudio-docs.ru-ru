---
title: Параметры, текстовый редактор, общие
description: Узнайте, как использовать страницу "Общие" для изменения глобальных параметров редактора кода и текста Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.Advanced
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e39febb27a74b0a2cef54098542bba087e2e0180
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943878"
---
# <a name="options-dialog-box-text-editor--general"></a>Диалоговое окно "Параметры": Текстовый редактор \> Общие

Это диалоговое окно позволяет изменять глобальные параметры для редактора кода и текста Visual Studio. Для вывода этого диалогового окна выберите пункт **Параметры** в меню **Сервис**, разверните папку **Текстовый редактор**, а затем щелкните **Общие**.

## <a name="settings"></a>Параметры

### <a name="drag-and-drop-text-editing"></a>Перетаскивание текста при редактировании

Если этот флажок установлен, вы можете переместить текст, выбрав и перетащив его мышью в другое расположение внутри текущего документа или в любой открытый документ.

### <a name="automatic-delimiter-highlighting"></a>Автоматически выделять разделители

Если этот флажок установлен, символы-разделители, отделяющие параметры или пары "элемент-значение", а также парные фигурные скобки, выделяются.

### <a name="track-changes"></a>Отслеживание изменений

При выборе редактора кода в поле выделения появляется желтая вертикальная линия, отмечающая код, который был изменен с момента последнего сохранения файла. При сохранении изменений вертикальные линии становятся зелеными.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Автоматически определять кодировку UTF-8 без сигнатуры

По умолчанию редактор определяет кодировку путем поиска меток порядка байтов или тегов наборов символов. Если их не удается найти в текущем документе, редактор кода пытается автоматически определить кодировку UTF-8 путем сканирования последовательностей байтов. Чтобы отключить автоматическое определение кодировки, снимите этот флажок.

### <a name="follow-project-coding-conventions"></a>Следовать рекомендациям по написанию кода проекта

Если выбрать этот параметр, соглашения о написании кода, указанные для проекта, переопределяют соглашения о написании кода, используемые вами в личных проектах.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Enable mouse-click to perform Go to Definition (Разрешить выполнение перехода к определению с помощью щелчка мыши)

Если выбран этот параметр, можно нажать клавишу **CTRL**, навести указатель мыши на элемент и щелкнуть его. При этом произойдет переход к определению выбранного элемента. Вы также можете выбрать клавиши **ALT** или **CTRL** + **ALT** в раскрывающемся списке **Use modifier key** (Использовать клавишу-модификатор).

Установите флажок **Открыть определение в быстром редакторе**, чтобы определение выбранного элемента отобразилось в окне без перехода из текущего расположения в редакторе кода.

## <a name="display"></a>Отображение

### <a name="selection-margin"></a>Поле выделения

Если этот флажок установлен, вдоль левого края области текста редактора отображается вертикальное поле. Можно щелкнуть это поле, чтобы выделить всю строку текста, или щелкнуть и перетащить последовательные строки текста.

|Поле выделения включено|Поле выделения выключено|
| - | - |
|![Снимок экрана HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Снимок экрана HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Поле индикаторов

Если этот флажок установлен, за левым краем области текста редактора отображается вертикальное поле. Если щелкнуть это поле, отображаются значок и подсказка, связанные с текстом. Например, в поле индикаторов отображаются ярлыки точки останова или списка задач. Сведения в поле индикаторов не выводятся на печать.

### <a name="highlight-current-line"></a>Выделение текущей строки

Если этот флажок установлен, вокруг строки кода, в которой находится курсор, отображается серый квадрат.

### <a name="show-structure-guide-lines"></a>Показать направляющие структуры

Если выбрать этот параметр, в редакторе отображаются вертикальные линии в соответствии со структурированными блоками кода. Это позволяет легко определять отдельные блоки кода.

### <a name="show-file-health-indicator"></a>Отображение индикатора работоспособности файлов

Если этот флажок установлен, в левом нижнем углу редактора будут отображаться строки состояния индикатора работоспособности файлов (ошибки, предупреждения) с параметрами очистки кода.

## <a name="see-also"></a>См. также

- ["Параметры", "Текстовый редактор", "Все языки"](../../ide/reference/options-text-editor-all-languages.md)
- ["Параметры", "Текстовый редактор", "Все языки", "Вкладки"](../../ide/reference/options-text-editor-all-languages-tabs.md)
- ["Параметры", "Текстовый редактор", "Расширение файла"](../../ide/reference/options-text-editor-file-extension.md)
- [Определение и настройка сочетаний клавиш](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Настройка редактора](../how-to-change-text-case-in-the-editor.md)
- [Использование технологии IntelliSense](../../ide/using-intellisense.md)
