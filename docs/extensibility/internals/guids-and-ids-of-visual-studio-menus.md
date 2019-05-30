---
title: Идентификаторы GUID и идентификаторы меню Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f858bec8ff025061603c72eda4ff6fc6d36549c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263630"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Меню идентификаторы GUID и идентификаторы Visual Studio
В этой статье перечисляет значения GUID и идентификатор меню и группы в строке меню Visual Studio. Эти значения определены в *.vsct* файлы, которые устанавливаются как часть Visual Studio SDK. Дополнительные сведения см. в разделе [команды, определенные в интегрированной среде разработки, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Дополнительные сведения о том, как работать с объектами Интегрированной среды разработки, которые определены в *.vsct* файлы, см. в разделе [расширить меню и команд](../../extensibility/extending-menus-and-commands.md).

 Меню и группы в строке меню Visual Studio используйте GUID `guidSHLMainMenu`. В самой строке меню имеет идентификатор `IDM_VS_TOOL_MAINMENU`.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Группы в строке меню Visual Studio
 Чтобы добавить меню в строку меню, в качестве одной из этих групп его родителя.

|Группа|ID|
|-----------|--------|
|Файл, редактирование, просмотр|IDG_VS_MM_FILEEDITVIEW|
|Рефакторинг|IDG_VS_MM_REFACTORING:|
|Проект|IDG_VS_MM_PROJECT|
|Построить|IDG_VS_MM_BUILDDEBUGRUN|
|Формат/Tools|IDG_VS_MM_TOOLSADDINS|
|Окна/Справка/сообщества|IDG_VS_MM_WINDOWHELP|
|Надстройки|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Меню в строке меню Visual Studio
 Чтобы добавить группу в существующее меню Visual Studio, задайте один из следующих меню с родительским. Подменю не включаются в этот список.

|Меню|ID|
|----------|--------|
|Файл|IDM_VS_MENU_FILE|
|Правка|IDM_VS_MENU_EDIT|
|Просмотр|IDM_VS_MENU_VIEW|
|Рефакторинг|IDM_VS_MENU_REFACTORING|
|Проект|IDM_VS_MENU_PROJECT|
|Построить|IDM_VS_MENU_BUILD|
|Формат|IDM_VS_MENU_FORMAT|
|Инструменты|IDM_VS_MENU_TOOLS|
|Расширения|IDM_VS_MENU_EXTENSIONS|
|Окно|IDM_VS_MENU_WINDOW|
|Надстройки|IDM_VS_MENU_ADDINS|
|Сообщество|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Группы меню Visual Studio
 В следующих списках приведены группы, полученные непосредственно из меню в строке меню Visual Studio. Самый быстрый способ добавить команду в меню Visual Studio — присвоить одной из этих групп в качестве родительского элемента. Группы, которые получены из подменю не отображаются в этом разделе.

### <a name="file-menu-groups"></a>Файловые группы меню

|Группа|ID|
|-----------|--------|
|Новый или открыть|IDG_VS_FILE_FILE|
|Add|IDG_VS_FILE_ADD|
|Решение|IDG_VS_FILE_SOLUTION|
|Прочее|IDG_VS_FILE_MISC|
|Сохранение|IDG_VS_FILE_SAVE|
|Переименовать|IDG_VS_FILE_RENAME|
|Браузер|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Самые последние использовавшиеся|IDG_VS_FILE_MRU|
|Перемещение|IDG_VS_FILE_MOVE|
|Exit|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Изменение группы меню

|Группа|ID|
|-----------|--------|
|Отменить/Повторить|IDG_VS_EDIT_UNDOREDO|
|Операции вырезания, копирования и вставки|IDG_VS_EDIT_CUTCOPY|
|Выбрать|IDG_VS_EDIT_SELECT|
|Оператор GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|Объекты|IDG_VS_EDIT_OBJECTS|
|Команды OLE|IDG_VS_EDIT_OLEVERBS|
|Команда также|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Рефакторинг группы меню

|Группа|ID|
|-----------|--------|
|Общие|IDG_REFACTORING_COMMON|
|Дополнительно|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Просмотр групп меню

|Группа|ID|
|-----------|--------|
|Код формы|IDG_VS_VIEW_FORMCODE|
|Браузер|IDG_VS_VIEW_BROWSER|
|Определение представлений|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Архитектор Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Организации Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Обозреватель кода|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Windows dev|IDG_VS_VIEW_DEV_WINDOWS|
|Панели инструментов|IDG_VS_VIEW_TOOLBARS|
|Символы|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Перейти|IDG_VS_VIEW_NAVIGATE|
|Мелкий перехода|IDG_VS_VIEW_SMALLNAVIGATE|
|Обозреватель объектов|IDG_VS_VIEW_OBJBRWSR|
|Команда также|IDG_VS_VIEW_COMMANDWELL|
|Страницы свойств|IDG_VS_VIEW_PROPPAGES|
|Обновление|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Группы меню проекта

|Группа|ID|
|-----------|--------|
|Прочие добавить|IDG_VS_PROJ_MISCADD|
|Add|IDG_VS_PROJ_ADD|
|Папка|IDG_VS_PROJ_FOLDER|
|Выгрузку/перезагрузку|IDG_VS_PROJ_UNLOADRELOAD|
|Ссылка|IDG_VS_PROJ_REFERENCE|
|Параметры|IDG_VS_PROJ_OPTIONS|
|Параметры|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Создание группы меню

|Группа|ID|
|-----------|--------|
|Решение|IDG_VS_BUILD_SOLUTION|
|Выбранное|IDG_VS_BUILD_SELECTION|
|Оптимизация с использованием профиля|IDG_VS_PGO_SELECTION|
|Прочее|IDG_VS_BUILD_MISC|
|Отмена|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Группы меню средств

|Группа|ID|
|-----------|--------|
|Командная строка|IDG_VS_TOOLS_CMDLINE|
|Фрагменты кода|IDG_VS_TOOLS_SNIPPETS|
|Подмножество объектов|IDG_VS_TOOLS_OBJSUBSET|
|Параметры|IDG_VS_TOOLS_OPTIONS|
|Другие 2|IDG_VS_TOOLS_OTHER2|
|Внешние инструменты|IDG_VS_TOOLS_EXT_TOOLS|
|Внешние настроек|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Группы меню окна

|Группа|ID|
|-----------|--------|
|Оператор new|IDG_VS_WINDOW_NEW|
|Закрепления и закрытия|IDG_VS_DOCKCLOSE|
|Закрепления или скрыть|IDG_VS_DOCKHIDE|
|Упорядочить|IDG_VS_WINDOW_ARRANGE|
|Навигация|IDG_VS_WINDOW_NAVIGATION|
|Список|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Группы меню справки

|Группа|ID|
|-----------|--------|
|Примеры|IDG_VS_HELP_SAMPLES|
|Поддержка|IDG_VS_HELP_SUPPORT|
|Общие сведения о|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Подменю из меню Visual Studio
 Следующая иерархия показывает подменю, которые связаны с меню в строке меню Visual Studio. Так, как только группа может включать меню в виде родительского, каждый подменю необходимо опускаются из группы, меню, вместо непосредственно из меню. Дополнительные сведения о связи между меню, подменю и групп см. в разделе [Добавление подменю в меню](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Имена меню в строке меню Visual Studio не отображаются отдельно в этой иерархии, так как их можно вывести из соглашения об именовании для групп в интегрированной среде разработки, следующим образом: *IDG_VS_\<имя меню\>_\<имя группы\>* .

|Родительская группа|Подменю|Дочерние группы|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1...6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>См. также
- [Идентификаторы GUID и идентификаторы Visual Studio панелей инструментов](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Идентификаторы GUID и идентификаторы Visual Studio команды](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio командные файлы table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
