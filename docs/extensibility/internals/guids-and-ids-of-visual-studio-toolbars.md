---
title: Идентификаторы GUID и идентификаторов панелей инструментов Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 394e0991d734279879df89422ac23fdd26899eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Идентификаторы GUID и идентификаторов панелей инструментов Visual Studio
В этом разделе перечисляются значения GUID и ID панелей инструментов, которые включены в среде разработки Visual Studio (IDE) и групп они содержат. Эти значения определяются в vsct-файлами, которые устанавливаются как часть пакета SDK для Visual Studio. Дополнительные сведения см. в разделе [IDE-Defined команд, меню и группы](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Многие из панели инструментов, доступные в Visual Studio не определены в Visual Studio, а также их GUID и ID значения не являются открытыми. В этом разделе перечислены только панелей инструментов, которые определены в пакет SDK для Visual Studio vsct-файлами.  
  
 Дополнительные сведения о работе с объектами интегрированной среды разработки, которые определены в vsct-файлами см. в разделе [расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
 Панели инструментов по умолчанию, предоставляемые в Интегрированной среде разработки Visual Studio используйте GUID `guidSHLMainMenu`, за исключением случаев, в противном случае значение задано с использованием синтаксиса GUID: ID.  
  
## <a name="ide-toolbars"></a>Панели инструментов интегрированной среды разработки  
 Следующие панели инструментов, предоставляемых Visual Studio IDE. Панели инструментов могут отображаться, выбирая их в **панели инструментов** подменю **средства** меню. Панели инструментов в окнах инструментов не включаются в этом разделе.  
  
 Только группы может просматривать непосредственно из панели инструментов. Чтобы добавить группу, присвоено значение родительского GUID и ID на панели инструментов. Чтобы добавить кнопку на панель инструментов, присвоено значение родительской группы на панели инструментов.  
  
|Toolbar|ID|  
|-------------|--------|  
|Стандартный|IDM_VS_TOOL_STANDARD|  
|Построить|IDM_VS_TOOL_BUILD|  
|Текстовый редактор|IDM_VS_TOOL_TEXTEDITOR|  
|Отладка|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Место отладки|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Специальные панели инструментов  
 Определенные этих панелей инструментов в интегрированной среде разработки Visual Studio, однако они служат специализированных функций и не размещайте группы команд.  
  
|Toolbar|ID|  
|-------------|--------|  
|Добавление команды|IDM_VS_TOOL_ADDCOMMAND|  
|Не определено|IDM_VS_TOOL_UNDEFINED|  
|схема XML|IDM_VS_TOOL_SCHEMA|  
|XML-данных|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Группы на панелях инструментов интегрированной среды разработки  
 Чтобы добавить кнопку на стандартной панели инструментов, установите одно из следующих групп с родительским. Группы с сортировкой по родительской панели инструментов.  
  
### <a name="standard-toolbar-groups"></a>Стандартная панель инструментов группы  
  
|name|ID|  
|----------|--------|  
|Сохранение и открытие|IDG_VS_TOOLSB_SAVEOPEN|  
|Вырезания или копирования|IDG_VS_TOOLSB_CUTCOPY|  
|Отменить/Повторить|IDG_VS_TOOLSB_UNDOREDO|  
|Запуск и сборки|IDG_VS_TOOLSB_RUNBUILD|  
|Поиск|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Новые окна|IDG_VS_TOOLSB_NEWWINDOWS|  
|Загрузки и сохранения|IDG_VS_WINDOWUI_LOADSAVE|  
|Датчик|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Построение группы на панели инструментов  
  
|name|ID|  
|----------|--------|  
|Панель построения|IDG_VS_BUILDBAR|  
|Отмена|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Панель инструментов редактора текстов групп  
  
|name|ID|  
|----------|--------|  
|Завершение|IDM_VS_TOOL_TEXTEDITOR|  
|Отступ|IDG_VS_EDITTOOLBAR_INDENT|  
|Комментарий|IDG_VS_EDITTOOLBAR_COMMENT|  
|Закладки|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Отладка инструментов группы  
  
|name|ID|  
|----------|--------|  
|Выполнение|IDM_DEBUG_TOOLBAR|  
|Отладка по шагам|IDG_DEBUG_TOOLBAR_STEPPING|  
|Контрольное значение|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Расположение группы инструментов отладки  
  
|name|ID|  
|----------|--------|  
|Место отладки|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Панели инструментов окна инструментов  
 Панели инструментов могут появляться непосредственно в Интегрированной среде разработки или в окнах инструментов **обозревателе решений**. Так как окна инструментов не определены в vsct-файлами, панели инструментов окна инструментов не имеют определенных родительских узлов. Вместо этого их следует разместить в коде. Следующая таблица показывает панели инструментов, которые отображаются в окнах инструментов в Интегрированной среде разработки и группы команд, содержащихся в них.  
  
> [!NOTE]
>  Панели инструментов и группы используйте GUID `guidSHLMainMenu`, за исключением случаев, в противном случае значение задано с использованием синтаксиса GUID: ID. Если для панели инструментов указан идентификатор GUID, это также относится к групп, которые получены из панели инструментов.  
  
|Окно инструментов|Toolbar|Группы|  
|-----------------|-------------|------------|  
|обозреватель решений|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|обозревателя серверов|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Свойства|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Представление классов|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Представление классов|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Обозреватель объектов|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Обозреватель объектов|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Вывод|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Поиск и замена|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Результаты поиска 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Результаты поиска 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Фрагмент кода|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Закладки|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|список задач|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Задачи пользователя|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Список ошибок|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Обозреватель вызовов|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Точки останова|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Дизассемблированный код|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Память 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Процессы|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>См. также  
 [Контроллер меню добавляется на панель инструментов](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Добавление панели инструментов в окне инструментов](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)