---
title: GUIDs и идентиматары Визуальные студии Toolbars (ru) Документы Майкрософт
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708231"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs и идентионные идентизаны панели инструментов Visual Studio
В этой теме перечисляются значения GUID и ID баров инструментов, включенных в интегрированную среду разработки Visual Studio (IDE), а также группы, которые они содержат. Эти значения определяются в *файлах .vsct,* которые устанавливаются как часть Визуальной студии SDK. Для получения дополнительной [информации](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)см.

> [!NOTE]
> Многие панели инструментов, доступные Visual Studio, не определяются Visual Studio, а их значения GUID и ID не являются общедоступными. В этой теме перечислены только панели инструментов, которые определяются в файлах Visual Studio SDK *.vsct.*

 Для получения дополнительной [информации](../../extensibility/extending-menus-and-commands.md)о том, как работать с объектами IDE, которые определены в файлах *.vsct,* см.

 Панели инструментов по умолчанию, предоставляемые Visual `guidSHLMainMenu`Studio IDE, `GUID:ID` используют GUID, за исключением случаев, когда иное указано с помощью синтаксиса.

## <a name="ide-toolbars"></a>Панели инструментов IDE
 Следующие панели инструментов предоставляются Visual Studio IDE. Панели инструментов могут отображаться, выбирая их в подменю **Toolbars** меню **Tools.** Панели инструментов в окнах инструментов не включены в этот раздел.

 Только группы могут спуститься непосредственно из панели инструментов. Чтобы добавить группу, установите ее родитель в GUID и ID панели инструментов. Чтобы добавить кнопку в панель инструментов, установите ее родителей в группу на панели инструментов.

|Панель инструментов|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Построение|IDM_VS_TOOL_BUILD|
|Текстовый редактор|IDM_VS_TOOL_TEXTEDITOR|
|Отладка|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Расположение дебага|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Специальные панели инструментов
 Эти панели инструментов определяются Visual Studio IDE, но они служат специализированным функциям и не размещают командные группы.

|Панель инструментов|ID|
|-------------|--------|
|Команда Add|IDM_VS_TOOL_ADDCOMMAND|
|Не определено.|IDM_VS_TOOL_UNDEFINED|
|схема XML|IDM_VS_TOOL_SCHEMA|
|XML-данные|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Группы на панели инструментов IDE
 Чтобы добавить кнопку в стандартную панель инструментов, установите одну из следующих групп в качестве ее родителя. Группы сортируются по родительской панели инструментов.

### <a name="standard-toolbar-groups"></a>Стандартные группы панели инструментов

|name|ID|
|----------|--------|
|Сохранить/Открыть|IDG_VS_TOOLSB_SAVEOPEN|
|Вырезать / Копировать|IDG_VS_TOOLSB_CUTCOPY|
|Отменить/Повторить|IDG_VS_TOOLSB_UNDOREDO|
|Выполнить/построить|IDG_VS_TOOLSB_RUNBUILD|
|Поиск|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Новые окна|IDG_VS_TOOLSB_NEWWINDOWS|
|Нагрузка/Сохранение|IDG_VS_WINDOWUI_LOADSAVE|
|Датчик|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Создание групп панели инструментов

|name|ID|
|----------|--------|
|Сборка бара|IDG_VS_BUILDBAR|
|Отмена|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Группы панели инструментов текстовых редакторов

|name|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Отступ|IDG_VS_EDITTOOLBAR_INDENT|
|Комментарий|IDG_VS_EDITTOOLBAR_COMMENT|
|Закладки|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Группы панели инструментов debug

|name|ID|
|----------|--------|
|Выполнение|IDM_DEBUG_TOOLBAR|
|Отладка по шагам|IDG_DEBUG_TOOLBAR_STEPPING|
|Контрольное значение|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Группы инструментов определения местоположения

|name|ID|
|----------|--------|
|Расположение дебага|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Панели инструментов окна инструментов
 Панели инструментов могут отображаться непосредственно в IDE или в окнах инструментов, таких как **Solution Explorer.** Поскольку окна инструментов не определены в файлах *.vsct,* панели инструментов не имеют определенных родителей. Вместо этого они помещаются в код. В следующей таблице показаны панели инструментов, которые появляются на окнах инструментов в IDE, и группы команд, которые они содержат.

> [!NOTE]
> Панели инструментов и группы используют GUID, `guidSHLMainMenu`за исключением случаев, когда иное указано с помощью синтаксиса GUID:ID. В тех случаях, когда GUID указан для панели инструментов, он также применяется к группам, которые спускаются с панели инструментов.

|Окно инструмента|Панель инструментов|Группы|
|-----------------|-------------|------------|
|Обозреватель решений|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1. 5|
|Обозреватель серверов|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Свойства|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Представление классов|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Представление классов|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Обозреватель объектов|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Обозреватель объектов|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Вывод|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Поиск и замена|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Найти результаты 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Результаты поиска 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Фрагмент кода|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Закладки|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|список задач|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Задачи пользователя|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Список ошибок|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Обозреватель вызовов|IDM_VS_TOOL_CALLBROWSER1. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Точки останова|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Дизассемблированный код|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Память 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1. 4<br /><br /> IDG_MEMORY_COLUMNS1. 4|
|Процессы|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>См. также
- [Добавление контроллера меню в панель инструментов](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Добавление панели инструментов в окно инструмента](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUIDs и идентиматы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
