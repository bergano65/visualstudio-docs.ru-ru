---
title: Страница “Параметры”, свойства узла “Среда”
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee14cddc6a3eb4b0348b88be1d7c2b0a48b44c01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945624"
---
# <a name="options-page-environment-node-properties"></a>Страница "Параметры", свойства узла "Среда"

В этой статье описываются некоторые из страниц (или коллекций свойств) диалогового окна **Параметры**, связанных с `DTE.Properties("Environment", <Property Page>)`, категория **Среда**. Заголовок каждого из подразделов представляет собой вызов, используемый для доступа к коллекции свойств, а таблицы содержат списки свойств в коллекции.

## <a name="general"></a>Общие

`DTE.Properties("Environment", "General")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|ShowStatusBar|Get/Set (Boolean)|Определяет, является ли строка состояния видимой.|
|WindowMenuContainsNItems|Get/Set (Short)|Определяет, как располагаются окна документов в нижней части меню «Окна».|
|MRUListContainsNItems|Get/Set (Short)|Определяет количество файлов, отображаемых во вложенном меню «Недавно использовавшиеся».|
|Анимации|Get/Set (Boolean)|Определяет, использует ли интегрированная среда разработки (IDE) анимацию в строке состояния.|
|AnimationSpeed|Get/Set (Short)||
|AutoAdjustExperience|Get/Set (Boolean)|Автоматически настраивает визуальное представление в зависимости от производительности клиента.|
|RichClientExperienceOptions|Get/Set (Enum)|Включает расширенное визуальное представление клиента, используя значения в <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (Boolean)|Определяет, отображается ли кнопка **Закрыть** только на активной вкладке.|
|AutohidePinActiveTabOnly|Get/Set (Boolean)|Определяет, применяется ли действие кнопки **Автоматически скрывать** только к активной вкладке.|

## <a name="add-inmacros-security"></a>Безопасность надстроек и макросов

`DTE.Properties("Environment", "AddinMacrosSecurity")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|MacrosEnabled|Get/Set (Boolean)|Разрешает выполнение макросов.|
|AddinsEnabled|Get/Set (Boolean)|Разрешает загрузку надстроек.|
|LoadAddinsFromTheWeb|Get/Set (Boolean)|Разрешает загрузку надстроек по URL-адресу в Интернете.|

## <a name="documents"></a>Документы

`DTE.Properties("Environment", "Documents")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|Определяет, использовать ли при открытии нового файла текущее окно документа, если текущий документ сохранен. `false` означает, что новый документ всегда следует открывать в новом окне.|
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|Определяет, должна ли среда автоматически перезагружать файлы, открытые в интегрированной среде разработки, если операционная система сообщает ей, что файлы на диске были изменены.|
|AutoloadExternalChanges|Get/Set (Boolean)|Определяет, будут ли обнаруженные внешние изменения открытых документов автоматически перезагружать измененный файл, если открытый документ не был изменен. Если изменения в открытый документ уже внесены и это свойство имеет значение `true`, интегрированная среда разработки предлагает действовать так же, как если бы свойство имело значение `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|Определяет, берет ли команда <xref:EnvDTE.DTEClass.OpenFile%2A> каталог и имя файла из последнего активного документа или из того места, откуда файл был открыт последний раз.|
|MiscFilesProjectSavesLastNItems|Get/Set (Short)|Определяет количество файлов, записываемое проектом «Прочие файлы». В результате при следующем использовании интегрированной среды разработки пользователь может увидеть, какой файл на диске был открыт последним в качестве прочего файла.|
|ShowMiscFilesProject|Get/Set (Boolean)|Определяет, отображается ли проект «Прочие файлы».|
|CheckForConsisentLineEndings|Get/Set (Boolean)|Проверяет наличие окончания строк при загрузке файла.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|Сохраняет документы в формате Юникод, если данные невозможно сохранить в выбранной кодировке.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|Выводит предупреждение, когда глобальная отмена затрагивает другие измененные файлы.|
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|Разрешает изменение файлов только для чтения, однако при попытке сохранить их выводит предупреждение.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Положение в списке вкладок, в которое вставляется открытый документ.|

## <a name="extension-manager"></a>диспетчер расширений

`DTE.Properties("Environment", "ExtensionManager")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boolean)|Загружает расширения пользователей при запуске Visual Studio от имени администратора. После изменения этого значения необходимо перезапустить Visual Studio.|
|EnableOnline|Get/Set (Boolean)|Предоставляет доступ к расширениям в Visual Studio Marketplace.|
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|Автоматически проверяет наличие обновлений для установленных расширений.|

## <a name="find-and-replace"></a>Поиск и замена

`DTE.Properties("Environment", "FindAndReplace")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|ShowWarningMessages|Get/Set (Boolean)|Отображает предупреждающие сообщения.|
|InitializeFromEditor|Get/Set (Boolean)|Автоматически заполняет поле **Найти** текстом из редактора.|
|ShowMessageBoxes|Get/Set (Boolean)|Отображает информационные сообщения.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|Скрывает окно **Поиск и замена** после нахождения соответствия с помощью функции **Быстрый поиск** или **Быстрая замена**.|

## <a name="import-and-export-settings"></a>Импорт и экспорт параметров

`DTE.Properties("Environment", "Import and Export Settings")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|TrackTeamSettings|Get/Set (Boolean)|Использует параметры в файле, заданном свойством TeamSettingsFile.|
|TeamSettingsFile|Get/Set (String)|Имя файла с параметрами рабочей группы.|
|AutoSaveFile|Get/Set (String)|Имя файла, в котором автоматически сохраняются параметры пользователя.|

## <a name="international-settings"></a>Выбор языка

`DTE.Properties("Environment", "International")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|Язык|Get/Set (String)|Значение кода языка для текущего языка для Visual Studio.|

## <a name="keyboard"></a>Клавиатура

`DTE.Properties("Environment", "Keyboard")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|Схема|Get/Set (String)|Возвращает строку, содержащую встроенную схему, строку, содержащую полный путь к загруженному VSK-файлу или «(Default)», если VSK-файл не загружен.|

## <a name="projects-and-solution"></a>Проекты и решения

`DTE.Properties("Environment", "ProjectsAndSolution")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|OnRunOrPreview|Get/Set (String)|Определяет, должна ли интегрированная среда разработки сохранять все свои файлы перед просмотром или запуском построенного приложения.|
|ProjectsLocation|Get/Set (String)|Определяет каталог по умолчанию, где сохраняются новые проекты.|
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|Определяет, отображать ли окно **Вывод** при начале сборки.|
|ShowTaskListAfterBuild|Get/Set (Boolean)|Определяет, должна ли неудавшаяся операция построения отображать **Список задач** по окончании сборки.|
|TrackFileSelectionInExplorer|Get/Set (Boolean)|Определяет, отслеживается ли текущий элемент в **обозревателе решений**.|
|AlwaysShowSolutionNode|Get/Set (Boolean)|Определяет, отображается ли узел решения.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|Определяет, ограничены ли операции сохранения только автозагружаемыми проектами и их зависимыми файлами.|
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|Определяет, отображаются ли расширенные конфигурации построения.|
|ConcurrentBuilds|Get/Set (String)|Определяет максимальное число параллельных сборок проекта.|
|SaveNewProjects|Get/Set (Boolean)|Определяет, сохраняются ли новые проекты автоматически после создания.|
|PromptForRenameSymbol|Get/Set (Boolean)|Указывает, запрашивать ли переименование символов при переименовании файлов.|
|OnRunWhenErrors|Get/Set (Enum)|Задает поведение при выполнении, когда построение завершено с ошибками.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Задает поведение при выполнении, когда проект устарел.|
|ProjectTemplatesLocation|Get/Set (String)|Каталог, содержащий шаблоны проектов пользователя.|
|ProjectItemTemplatesLocation|Get/Set (String)|Каталог, содержащий шаблоны элементов пользователя.|
|DefaultBehaviorForStartupProjects|Get/Set (String)||
|MSBuildOutputVerbosity|Get/Set (String)|Задает уровень детализации выходных данных построения.|

## <a name="startup"></a>Запуск

`DTE.Properties("Environment", "Startup")`

::: moniker range="vs-2017"

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Действие, выполняемое при запуске из <xref:EnvDTE.vsStartUp> со значениями от 0 до 5:<br /><br /> — 0: открыть домашнюю страницу<br />— 1: загрузить последнее загружавшееся решение<br />— 2: показать диалоговое окно **Открытие проекта**<br />— 3: показать диалоговое окно **Создание проекта**<br />— 4: показать пустую среду<br />— 5: показать начальную страницу|
|StartPageRSSUrl|Get/Set (String)|URL-адрес RSS-канала, используемый при запуске.|
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|Обновляет начальную страницу каждый раз по истечении интервала, заданного свойством StartPageRefreshInterval.|
|StartPageRefreshInterval|Get/Set (Short)|Интервал обновления начальной страницы в минутах.|

::: moniker-end

::: moniker range=">=vs-2019"

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Действие, выполняемое при запуске из <xref:EnvDTE.vsStartUp>.|

::: moniker-end

## <a name="tasklist"></a>TaskList

`DTE.Properties("Environment", "TaskList")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boolean)|Указывает, запрашивать ли подтверждение при удалении задач из **списка задач**.|
|WarnOnAddingHiddenItem|Get/Set (Boolean)|Указывает, выводить ли предупреждение при добавлении пользовательской задачи, которая не будет отображаться.|
|DontShowFilePaths|Get/Set (Boolean)|Указывает, следует ли отображать полные пути к файлам в списке задач.|
|CommentTokens|SafeArray|Возвращает SafeArray значений маркера комментариев. Каждое имеет поля,`Name`(string) и`Priority` (<xref:EnvDTE.vsTaskPriority>, высокий, средний или низкий).|

## <a name="web-browser"></a>Веб-браузер

`DTE.Properties("Environment", "WebBrowser")`

|Имя элемента свойства|Значение|Описание|
| - |-----------|-----------------|
|HomePage|Get/Set (String)|Представляет URL-адрес домашней страницы.|
|SearchPage|Get/Set (String)|Представляет URL-адрес страницы поиска.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (источник, разработка, внешний).|
|ViewSourceExternalProgram|Get/Set (String)|Путь к внешнему средству просмотра исходного кода.|

## <a name="see-also"></a>См. также

- [Управление параметрами](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Определение имен элементов свойств на страницах параметров](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Страница "Параметры", свойства узла "Шрифты и цвета"](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Страница "Параметры", свойства узла "Текстовый редактор"](../../ide/reference/options-page-text-editor-node-properties.md)
- [Диалоговое окно "Параметры среды"](../../ide/reference/environment-options-dialog-box.md)