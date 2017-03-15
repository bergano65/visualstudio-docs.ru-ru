---
title: "Параметры, текстовый редактор, общие | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "Параметры - диалоговое окно (текстовый редактор)"
  - "Редактор кода"
  - "Текстовый редактор [Visual Studio]"
  - "редакторы, глобальные параметры"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Параметры, текстовый редактор, общие
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом диалоговом окне можно менять общие параметры для редактора кода и текстового редактора [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Чтобы открыть это диалоговое окно, в меню **Сервис** выберите пункт **Параметры**, разверните папку **Текстовый редактор** и щелкните **Общие**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих настроек или выпуска.  Чтобы изменить параметры, в меню **Сервис** выберите команду **Импорт и экспорт параметров**.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Параметры  
 Разрешить перетаскивание текста при редактировании  
 Этот параметр позволяет перемещать текст в другое место документа или в другой открытый документ путем перетаскивания мышью.  
  
 Автоматически выделять разделители  
 При выборе этого параметра выделяются символы, разделяющие параметры или пары элемент\-значение, а также парные фигурные скобки.  
  
 Исправления  
 Когда редактор кода выбора в поле выделения отмечены вертикальная линия желтая код, который был изменен с момента последнего был сохранен файл.  При сохранении изменений, вертикальные линии будут зеленого.  
  
 Автоматически определять кодировку UTF\-8 без сигнатуры  
 По умолчанию редактор определяет кодировку путем поиска меток порядка следования байтов или тегов набора знаков.  Если ни один из этих элементов не найден в текущем документе, редактор кода предпринимает попытку автоматического определения кодировки UTF\-8 путем считывания последовательностей байтов.  Чтобы отключить автоматическое определение кодировки, не устанавливайте этот параметр.  
  
## Отображение  
 Поле структуры  
 При выборе этого параметра вдоль левого края текстовой области редактора отображается вертикальное поле.  Можно выделить строку текста, щелкнув это поле, либо несколько последовательных строк путем перетаскивания.  
  
|Флажок "Поле структуры" установлен|Флажок "Поле структуры" не установлен|  
|----------------------------------------|-------------------------------------------|  
|![Снимок экрана HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![Снимок экрана HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Поле индикаторов  
 При выборе этого параметра снаружи левого края текстовой области редактора отображается вертикальное поле.  Если щелкнуть это поле, появятся связанные с текстом значок и всплывающая подсказка.  Например, в поле индикаторов отображаются ярлыки точек останова и списка задач.  Сведения, отображаемые в поле индикаторов, не выводятся на печать.  
  
 Вертикальная полоса прокрутки  
 При выборе этого параметра отображается вертикальная полоса прокрутки, позволяющая выполнять прокрутку вверх и вниз при просмотре элементов, выходящих за пределы видимой области редактора.  Если вертикальные полосы прокрутки недоступны, для прокручивания содержимого можно пользоваться клавишами PAGE UP, PAGE DOWN и клавишами управления курсором.  
  
 Горизонтальная полоса прокрутки  
 При выборе данного элемента управления отображается горизонтальная полоса прокрутки, позволяющая выполнять прокрутку из стороны в сторону при просмотре элементов, выходящих за пределы видимой области редактора.  Если горизонтальные полосы прокрутки недоступны, для прокручивания содержимого можно пользоваться клавишами управления курсором.  
  
 Линия выделения текущая  
 Отображает серое окно вокруг выбранного строки кода, в которой находится курсор.  
  
## См. также  
 [Параметры, текстовый редактор, все языки](../../ide/reference/options-text-editor-all-languages.md)   
 ["Параметры", "Текстовый редактор", "Все языки", "Вкладки"](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 ["Параметры", "Текстовый редактор", "Расширение файла"](../../ide/reference/options-text-editor-file-extension.md)   
 [Определение и настройка сочетаний клавиш](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Настройка редактора](../../ide/customizing-the-editor.md)   
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)