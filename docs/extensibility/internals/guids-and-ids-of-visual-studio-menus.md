---
title: "Идентификаторы GUID и идентификаторы меню Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "меню Visual studio"
  - "группы Visual studio"
  - "id"
  - "существующие меню"
  - "Идентификатор GUID"
  - "меню"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Идентификаторы GUID и идентификаторы меню Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом разделе перечисляет значения GUID и идентификатор меню и группы в строке меню Visual Studio. Эти значения определяются в vsct\-файлы, которые устанавливаются как часть пакета SDK для Visual Studio. Дополнительные сведения см. в разделе [Команды, определенные в интегрированной среде разработки, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Дополнительные сведения о работе с объектами Интегрированной среды разработки, определенные в vsct\-файлах см. в разделе [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
 Меню и группы в строке меню Visual Studio используйте GUID `guidSHLMainMenu`. В меню самого имеет идентификатор `IDM_VS_TOOL_MAINMENU`.  
  
## Группы в строке меню Visual Studio  
 Чтобы добавить меню в строке меню, задайте одно из этих групп с родительским.  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Файл, представления и изменения|IDG\_VS\_MM\_FILEEDITVIEW|  
|Рефакторинг|IDG\_VS\_MM\_REFACTORING:|  
|Проект|IDG\_VS\_MM\_PROJECT|  
|Сборка|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|Формат и средства|IDG\_VS\_MM\_TOOLSADDINS|  
|Окна, Справка и сообщество|IDG\_VS\_MM\_WINDOWHELP|  
|Надстройки|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Меню в строке меню Visual Studio  
 Чтобы добавить группу к существующему меню Visual Studio, задайте одно из следующих меню с родительским. Подменю не включаются в этот список.  
  
|Меню|Идентификатор|  
|----------|-------------------|  
|Файл|IDM\_VS\_MENU\_FILE|  
|Правка|IDM\_VS\_MENU\_EDIT|  
|Просмотр|IDM\_VS\_MENU\_VIEW|  
|Рефакторинг|IDM\_VS\_MENU\_REFACTORING|  
|Проект|IDM\_VS\_MENU\_PROJECT|  
|Сборка|IDM\_VS\_MENU\_BUILD|  
|Формат|IDM\_VS\_MENU\_FORMAT|  
|Инструменты|IDM\_VS\_MENU\_TOOLS|  
|Окно|IDM\_VS\_MENU\_WINDOW|  
|Надстройки|IDM\_VS\_MENU\_ADDINS|  
|Сообщество|IDM\_VS\_MENU\_COMMUNITY|  
|Справка|IDM\_VS\_MENU\_HELP|  
  
## Группы меню Visual Studio  
 Ниже приведена групп, полученные непосредственно из меню в строке меню Visual Studio. Самый быстрый способ добавить команды в меню Visual Studio является одной из этих групп задан как родительский. Группы, которые получены из подменю не отображаются в этом разделе.  
  
### Файловые группы меню  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Новый или открыть|IDG\_VS\_FILE\_FILE|  
|Add|IDG\_VS\_FILE\_ADD|  
|Решение|IDG\_VS\_FILE\_SOLUTION|  
|Прочее|IDG\_VS\_FILE\_MISC|  
|Сохранить|IDG\_VS\_FILE\_SAVE|  
|Переименовать|IDG\_VS\_FILE\_RENAME|  
|Браузер|IDG\_VS\_FILE\_BROWSER|  
|Печать|IDG\_VS\_FILE\_PRINT|  
|Самые последние использовавшиеся|IDG\_VS\_FILE\_MRU|  
|Перемещение|IDG\_VS\_FILE\_MOVE|  
|Exit|IDG\_VS\_FILE\_EXIT|  
  
### Изменение группы меню  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Отменить\/Повторить|IDG\_VS\_EDIT\_UNDOREDO|  
|Вырезания, копирования и вставки|IDG\_VS\_EDIT\_CUTCOPY|  
|Выбрать|IDG\_VS\_EDIT\_SELECT|  
|GoTo|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|объектов|IDG\_VS\_EDIT\_OBJECTS|  
|Команды OLE|IDG\_VS\_EDIT\_OLEVERBS|  
|Команда также|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### Рефакторинг группы меню  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Common|IDG\_REFACTORING\_COMMON|  
|Дополнительно|IDG\_REFACTORING\_ADVANCED|  
  
### Просмотр групп меню  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Код формы|IDG\_VS\_VIEW\_FORMCODE|  
|Браузер|IDG\_VS\_VIEW\_BROWSER|  
|Определение представлений|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Архитектор Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|Организации Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|Обозреватель кода|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Разработчиков Windows|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|Панели инструментов|IDG\_VS\_VIEW\_TOOLBARS|  
|Символы|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|Перейти|IDG\_VS\_VIEW\_NAVIGATE|  
|Небольшой перехода|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|Обозреватель объектов|IDG\_VS\_VIEW\_OBJBRWSR|  
|Команда также|IDG\_VS\_VIEW\_COMMANDWELL|  
|Страницы свойств|IDG\_VS\_VIEW\_PROPPAGES|  
|Обновить|IDG\_VS\_VIEW\_REFRESH|  
  
### Группы меню проекта  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Прочие добавить|IDG\_VS\_PROJ\_MISCADD|  
|Add|IDG\_VS\_PROJ\_ADD|  
|Папка|IDG\_VS\_PROJ\_FOLDER|  
|Выгрузка и перезагрузка|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|Ссылки|IDG\_VS\_PROJ\_REFERENCE|  
|Параметры|IDG\_VS\_PROJ\_OPTIONS|  
|Настройки|IDG\_VS\_PROJ\_SETTINGS|  
  
### Построение группы меню  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Решение|IDG\_VS\_BUILD\_SOLUTION|  
|Выбранное|IDG\_VS\_BUILD\_SELECTION|  
|Профильная оптимизация|IDG\_VS\_PGO\_SELECTION|  
|Прочее|IDG\_VS\_BUILD\_MISC|  
|Cancel|IDG\_VS\_BUILD\_CANCEL|  
  
### Группы меню средства  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Командная строка|IDG\_VS\_TOOLS\_CMDLINE|  
|Фрагменты кода|IDG\_VS\_TOOLS\_SNIPPETS|  
|Подмножество объектов|IDG\_VS\_TOOLS\_OBJSUBSET|  
|Параметры|IDG\_VS\_TOOLS\_OPTIONS|  
|Другие 2|IDG\_VS\_TOOLS\_OTHER2|  
|Внешние средства|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|Внешние настроек|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### Группы меню окна  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Новый|IDG\_VS\_WINDOW\_NEW|  
|Закрепление и закрыть|IDG\_VS\_DOCKCLOSE|  
|Закрепить или скрыть|IDG\_VS\_DOCKHIDE|  
|Упорядочить|IDG\_VS\_WINDOW\_ARRANGE|  
|Навигация|IDG\_VS\_WINDOW\_NAVIGATION|  
|Список|IDG\_VS\_WINDOW\_LIST|  
  
### Группы меню справки  
  
|Группа|Идентификатор|  
|------------|-------------------|  
|Примеры|IDG\_VS\_HELP\_SAMPLES|  
|Поддержка|IDG\_VS\_HELP\_SUPPORT|  
|О программе|IDG\_VS\_HELP\_ABOUT|  
  
## Подменю из меню Visual Studio  
 Следующая иерархия показывает подменю, которые связаны с меню в строке меню Visual Studio. Поскольку только в группе может быть как его родительский элемент меню, каждый подменю необходимо опускаются из группы меню, вместо непосредственно из меню. Дополнительные сведения о связи между меню, групп и вложенных меню в разделе [Добавление подменю в меню](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Имена меню в строке меню Visual Studio не отображаются отдельно в этой иерархии, так как они может быть выведен из соглашение об именах для групп в Интегрированной среде разработки, следующим образом: IDG\_VS\_*имя меню*\_*имя группы*.  
  
|Родительская группа|Подменю|Дочерние группы|  
|-------------------------|-------------|---------------------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1... 6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## См. также  
 [GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)