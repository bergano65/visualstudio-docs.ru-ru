---
title: "GUID и идентификаторы панелей инструментов Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы Visual studio"
  - "панели инструментов"
  - "панель инструментов Visual studio"
  - "id"
  - "toolgar группы"
  - "панели инструментов окна инструментов"
  - "Идентификатор GUID"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# GUID и идентификаторы панелей инструментов Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом подразделе перечисляются значения идентификатора GUID и панелей инструментов, включенных в интегрированной среде разработки \(ide\) Visual Studio и групп, которые они содержат.  Эти значения определяются в файлах .vsct, которые устанавливаются как часть пакета SDK для Visual Studio.  Дополнительные сведения см. в разделе [Команды, определенные в интегрированной среде разработки, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Большинство панелей инструментов, доступных в Visual Studio не указаны Visual Studio и их значения идентификатора GUID и не являются открытыми.  В этом разделе перечислены только панели инструментов, определенные в файлах пакета SDK .vsct Visual Studio.  
  
 Дополнительные сведения о том, как работать с объектами среды разработки, которые определены в файлах .vsct см. в разделе [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
 По умолчанию панель инструментов, предоставляемых средой разработки Visual Studio используют идентификаторы GUID `guidSHLMainMenu`, за исключением случаев, когда указано иное, используя идентификатор GUID: Синтаксис идентификатор.  
  
## Панели инструментов интегрированной среды разработки  
 Следующие панели инструментов, предоставляемых средой разработки Visual Studio.  Панели инструментов могут отображаться путем выбора их на **панели инструментов** подменю  **Сервис** меню.  Панели инструментов в окнах инструментов не включаются в этом разделе.  
  
 Только команды могут спустить непосредственно из панелей инструментов.  Чтобы добавить группу, установите его родительский идентификатор GUID и на панели инструментов.  Чтобы добавить кнопку на панели инструментов задайте его родительским элементом в группе на панели инструментов.  
  
|Панель инструментов|Идентификатор|  
|-------------------------|-------------------|  
|Standard|IDM\_VS\_TOOL\_STANDARD|  
|Построение|IDM\_VS\_TOOL\_BUILD|  
|Текстовый редактор|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Отладочная информация|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|Место отладки|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### Специальные панели инструментов  
 Эти панели инструментов определяются средой разработки Visual Studio, однако они служат специализированные функции и не делают группы команд основного приложения.  
  
|Панель инструментов|Идентификатор|  
|-------------------------|-------------------|  
|Добавьте команда|IDM\_VS\_TOOL\_ADDCOMMAND|  
|Не определено|IDM\_VS\_TOOL\_UNDEFINED|  
|Схема XML|IDM\_VS\_TOOL\_SCHEMA|  
|XML\-данные|IDM\_VS\_TOOL\_DATA|  
  
## Группы на панелях инструментов интегрированной среды разработки  
 Чтобы добавить кнопку к стандартной панели инструментов задайте одну из следующих групп в качестве его родительским элементом.  Группы упорядочены родительский элемент панели инструментов.  
  
### Группы стандартной панели инструментов  
  
|Имя|Идентификатор|  
|---------|-------------------|  
|Сохраните открытый\/|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|Вырезать или копировать|IDG\_VS\_TOOLSB\_CUTCOPY|  
|Отменить\/повторить|IDG\_VS\_TOOLSB\_UNDOREDO|  
|Выполнить\/построения|IDG\_VS\_TOOLSB\_RUNBUILD|  
|Поиск|IDG\_VS\_TOOLSB\_SEARCH|  
|Окна|IDG\_VS\_TOOLSB\_WINDOWS|  
|Новые окна|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|Загрузка и сохранение|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|Датчик|IDG\_VS\_TOOLSB\_GAUGE|  
  
### Группы панели инструментов построения  
  
|Имя|Идентификатор|  
|---------|-------------------|  
|Линейчатая построения|IDG\_VS\_BUILDBAR|  
|Отмена|IDG\_VS\_BUILD\_CANCEL|  
  
### Группы панели инструментов текстового редактора  
  
|Имя|Идентификатор|  
|---------|-------------------|  
|Выполнение|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Отступ|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|Комментарий|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|Закладки|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### Группы панели инструментов отладка  
  
|Имя|Идентификатор|  
|---------|-------------------|  
|Выполнение|IDM\_DEBUG\_TOOLBAR|  
|Отладка по шагам|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|Окна|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### Группы панели инструментов место отладки  
  
|Имя|Идентификатор|  
|---------|-------------------|  
|Расположение отладка|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## На панели инструментов окна инструментов  
 Панели инструментов могут встречаться непосредственно в интегрированную среду разработки или в окне инструментов как **Обозреватель решений**.  Поскольку окна инструментов не определены в файлах .vsct, панели инструментов окна инструментов не указан родительские элементы.  Вместо этого они помещаются в коде.  В следующей таблице показаны панели инструментов, которые отображаются в окне инструментов в интегрированной среде разработки и группы команд, которые они содержат.  
  
> [!NOTE]
>  Панели инструментов и группы используют идентификаторы GUID `guidSHLMainMenu`, за исключением случаев, когда указано иное, используя идентификатор GUID: Синтаксис идентификатор.  Идентификатор GUID для панели инструментов, где указано, оно также применяется к группам, опускаются из этой панели инструментов.  
  
|Окно инструментов|Панель инструментов|Groups|  
|-----------------------|-------------------------|------------|  
|Обозреватель решений|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|Обозреватель серверов|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|Свойства|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|Окно классов|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|Окно классов|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEARCH2|  
|Обозреватель объектов|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|Обозреватель объектов|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEARCH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|Поиск и замена|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|Результаты поиска 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|Результаты поиска 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|Закладки|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|Список задач|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|Задачи пользователя|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|Список ошибок|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|Обозреватель вызовов|IDM\_VS\_TOOL\_CALLBROWSER1..16|IDG\_VS\_TOOLBAR\_CALLBROWSER1\_ACTIONS<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_TYPE<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_CBSETTINGS|  
|Точки останова|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|Дизассемблированный код|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|Память 1\-4|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_COLUMNS1..4|  
|Процессы|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXECCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## См. также  
 [Добавление контроллера меню панели инструментов](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Добавление панели инструментов в окне инструментов](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)