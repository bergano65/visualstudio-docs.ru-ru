---
title: "&quot;Параметры&quot;, &quot;Текстовый редактор&quot;, &quot;Общие&quot; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: eee3b34e9f473c200463b65f1b839416f5dce0ec
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-general"></a>Параметры, текстовый редактор, общие
Это диалоговое окно позволяет изменять глобальные параметры для редактора кода и текста [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Для вывода этого диалогового окна щелкните элемент **Параметры** в меню **Сервис**, разверните папку **Текстовый редактор**, а затем щелкните **Общие**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="settings"></a>Параметры  
 Перетаскивание текста при редактировании  
 Если этот флажок установлен, вы можете переместить текст, выбрав и перетащив его мышью в другое расположение внутри текущего документа или в любой открытый документ.  
  
 Автоматически выделять разделители  
 Если этот флажок установлен, символы-разделители, отделяющие параметры или пары "элемент-значение", а также парные фигурные скобки, выделяются.  
  
 Отслеживание изменений  
 При выборе редактора кода в поле выделения появляется желтая вертикальная линия, отмечающая код, который был изменен с момента последнего сохранения файла. При сохранении изменений вертикальные линии становятся зелеными.  
  
 Автоматически определять кодировку UTF-8 без сигнатуры  
 По умолчанию редактор определяет кодировку путем поиска меток порядка байтов или тегов наборов символов. Если их не удается найти в текущем документе, редактор кода пытается автоматически определить кодировку UTF-8 путем сканирования последовательностей байтов. Чтобы отключить автоматическое определение кодировки, снимите этот флажок.  
  
## <a name="display"></a>Показать  
 Поле выделения  
 Если этот флажок установлен, вдоль левого края области текста редактора отображается вертикальное поле. Можно щелкнуть это поле, чтобы выделить всю строку текста, или щелкнуть и перетащить последовательные строки текста.  
  
|Поле выделения включено|Поле выделения выключено|  
|-------------------------|--------------------------|  
|![HTMLpageSelectionMarginOn screenshot](~/docs/ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff screenshot](~/docs/ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Поле индикаторов  
 Если этот флажок установлен, за левым краем области текста редактора отображается вертикальное поле. Если щелкнуть это поле, отображаются значок и подсказка, связанные с текстом. Например, в поле индикаторов отображаются ярлыки точки останова или списка задач. Сведения в поле индикаторов не выводятся на печать.  
  
 Вертикальная полоса прокрутки  
 Если этот флажок установлен, отображается вертикальная полоса прокрутки, позволяющая выполнять прокрутку вверх и вниз при просмотре элементов, выходящих за пределы видимой области редактора. Если вертикальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши PAGE UP, PAGE DOWN и клавиши управления курсором.  
  
 Горизонтальная полоса прокрутки  
 Если этот флажок установлен, отображается горизонтальная полоса прокрутки, позволяющая выполнять прокрутку вправо и влево при просмотре элементов, выходящих за пределы видимой области редактора. Если горизонтальные полосы прокрутки недоступны, для прокрутки можно использовать клавиши управления курсором.  
  
 Выделение текущей строки  
 Если этот флажок установлен, вокруг строки кода, в которой находится курсор, отображается серый квадрат.  
  
## <a name="see-also"></a>См. также  
 ["Параметры", "Текстовый редактор", "Все языки"](../../ide/reference/options-text-editor-all-languages.md)   
 ["Параметры", "Текстовый редактор", "Все языки", "Табуляция"](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 ["Параметры", "Текстовый редактор", "Расширение файла"](../../ide/reference/options-text-editor-file-extension.md)   
 [Определение и настройка сочетаний клавиш](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Настройка редактора](../../ide/customizing-the-editor.md)   
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)
