---
title: GUIDs и идентионные идентизация визуальных studio Меню (ru) Документы Майкрософт
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708240"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs и идентиматы меню Visual Studio
В этой статье перечисляется значения GUID и ID меню и групп в меню Visual Studio. Эти значения определяются в *файлах .vsct,* которые устанавливаются как часть Визуальной студии SDK. Для получения дополнительной [информации](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)см.

 Для получения дополнительной [информации](../../extensibility/extending-menus-and-commands.md)о том, как работать с интегрированными объектами среды разработки (IDE), которые определяются в файлах *.vsct,* см.

 Меню и группы в баре меню Visual `guidSHLMainMenu`Studio используют GUID. Сам бар меню имеет `IDM_VS_TOOL_MAINMENU`id.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Группы в меню Visual Studio
 Чтобы добавить меню в панель меню, установите одну из этих групп в качестве ее родителя.

|Группа|ID|
|-----------|--------|
|Файл/Отожоблик/Просмотр|IDG_VS_MM_FILEEDITVIEW|
|Рефакторинг|IDG_VS_MM_REFACTORING:|
|Проект|IDG_VS_MM_PROJECT|
|Построение|IDG_VS_MM_BUILDDEBUGRUN|
|Формат/Инструменты|IDG_VS_MM_TOOLSADDINS|
|Окно/Помощь/Сообщество|IDG_VS_MM_WINDOWHELP|
|Надстройки|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Меню в меню -13.09.2017
 Чтобы добавить группу в существующее меню Visual Studio, установите одно из следующих меню в качестве его родителя. Submenus не включены в этот список.

|Меню|ID|
|----------|--------|
|Файл|IDM_VS_MENU_FILE|
|Изменить|IDM_VS_MENU_EDIT|
|Просмотр|IDM_VS_MENU_VIEW|
|Рефакторинг|IDM_VS_MENU_REFACTORING|
|Проект|IDM_VS_MENU_PROJECT|
|Построение|IDM_VS_MENU_BUILD|
|Формат|IDM_VS_MENU_FORMAT|
|Инструменты|IDM_VS_MENU_TOOLS|
|Расширения|IDM_VS_MENU_EXTENSIONS|
|Окно|IDM_VS_MENU_WINDOW|
|Надстройки|IDM_VS_MENU_ADDINS|
|Сообщество|IDM_VS_MENU_COMMUNITY|
|Справка|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Группы по меню Visual Studio
 Ниже приведены группы, которые спускаются непосредственно из меню в меню Visual Studio. Самый быстрый способ добавить команду в меню Visual Studio — установить одну из этих групп в качестве родительской группы. Группы, которые происходят из подменю, не отображаются в этом разделе.

### <a name="file-menu-groups"></a>Группы меню файлов

|Группа|ID|
|-----------|--------|
|Новое/Открытое|IDG_VS_FILE_FILE|
|Добавить|IDG_VS_FILE_ADD|
|Решение|IDG_VS_FILE_SOLUTION|
|Разное|IDG_VS_FILE_MISC|
|Сохранять|IDG_VS_FILE_SAVE|
|Переименовать|IDG_VS_FILE_RENAME|
|Браузер|IDG_VS_FILE_BROWSER|
|Оператор print|IDG_VS_FILE_PRINT|
|Самые недавно использованные|IDG_VS_FILE_MRU|
|Переместить|IDG_VS_FILE_MOVE|
|Выход|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Элементы меню группы

|Группа|ID|
|-----------|--------|
|Отменить/Повторить|IDG_VS_EDIT_UNDOREDO|
|Вырезать /Копировать/вставить|IDG_VS_EDIT_CUTCOPY|
|Выберите пункт|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Поиск|IDG_VS_EDIT_FIND|
|Объекты|IDG_VS_EDIT_OBJECTS|
|OLE Глаголы|IDG_VS_EDIT_OLEVERBS|
|Командование Ну|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Группы меню рефактора

|Группа|ID|
|-----------|--------|
|Распространенные|IDG_REFACTORING_COMMON|
|Дополнительно|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Просмотр групп меню

|Группа|ID|
|-----------|--------|
|Код формы|IDG_VS_VIEW_FORMCODE|
|Браузер|IDG_VS_VIEW_BROWSER|
|Определение представлений|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Архитектор Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Организация Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Код браузера|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Дев Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Панели инструментов|IDG_VS_VIEW_TOOLBARS|
|Символы|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Перейти.|IDG_VS_VIEW_NAVIGATE|
|Малый Навигация|IDG_VS_VIEW_SMALLNAVIGATE|
|Обозреватель объектов|IDG_VS_VIEW_OBJBRWSR|
|Командование Ну|IDG_VS_VIEW_COMMANDWELL|
|Страницы свойств|IDG_VS_VIEW_PROPPAGES|
|Обновить|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Группы меню проекта

|Группа|ID|
|-----------|--------|
|Разное добавление|IDG_VS_PROJ_MISCADD|
|Добавить|IDG_VS_PROJ_ADD|
|Папка|IDG_VS_PROJ_FOLDER|
|Выгрузка/перезагрузка|IDG_VS_PROJ_UNLOADRELOAD|
|Справочник|IDG_VS_PROJ_REFERENCE|
|Параметры|IDG_VS_PROJ_OPTIONS|
|Параметры|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Создание групп меню

|Группа|ID|
|-----------|--------|
|Решение|IDG_VS_BUILD_SOLUTION|
|Выбор|IDG_VS_BUILD_SELECTION|
|Оптимизация с использованием профиля|IDG_VS_PGO_SELECTION|
|Прочее|IDG_VS_BUILD_MISC|
|Отмена|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Группы меню инструментов

|Группа|ID|
|-----------|--------|
|Командная строка|IDG_VS_TOOLS_CMDLINE|
|Фрагменты кода|IDG_VS_TOOLS_SNIPPETS|
|Подмножество объектов|IDG_VS_TOOLS_OBJSUBSET|
|Параметры|IDG_VS_TOOLS_OPTIONS|
|Другие 2|IDG_VS_TOOLS_OTHER2|
|Внешние инструменты|IDG_VS_TOOLS_EXT_TOOLS|
|Внешние настройки|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Группы меню окон

|Группа|ID|
|-----------|--------|
|Оператор new|IDG_VS_WINDOW_NEW|
|Док/Клоуз|IDG_VS_DOCKCLOSE|
|Док/Скрыть|IDG_VS_DOCKHIDE|
|Упорядочить|IDG_VS_WINDOW_ARRANGE|
|Навигации|IDG_VS_WINDOW_NAVIGATION|
|Список|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Группы меню справки

|Группа|ID|
|-----------|--------|
|Примеры|IDG_VS_HELP_SAMPLES|
|Поддержка|IDG_VS_HELP_SUPPORT|
|Сведения|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Подменю меню Visual Studio
 В следующей иерархии показаны подменю, связанные с меню в панели меню Visual Studio. Поскольку только группа может иметь меню в качестве своего родителя, каждое подменю должно происходить из группы в меню, а не непосредственно из меню. Для получения дополнительной информации о взаимосвязи между меню, группами и подменю, [см.](../../extensibility/adding-a-submenu-to-a-menu.md)

> [!NOTE]
> Названия меню в панели меню Visual Studio не отображаются отдельно в этой иерархии, поскольку они могут быть выведены из конвенции о наименовании для групп в IDE, следующим образом: *\<IDG_VS_ название\>меню и\<название\>группы*.

|Родительская группа|Submenu|Детские группы|
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
|||IDG_VS_WNDO_OTRWNDWS1... 6|
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
- [GUIDs и идентионные идентизаны панели инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUIDs и идентионные идентионности команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Таблица команд Visual Studio (.vsct) файлов](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
