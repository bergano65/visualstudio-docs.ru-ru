---
title: "Настройка изолированной оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>Настройка изолированной оболочки
Приложения Visual Studio изолированной оболочки можно настроить, изменив различных аспектов пользовательского интерфейса Visual Studio и ограничив команд и функций, включенных в специализированные приложения.  
  
## <a name="using-the-applicationpkgdef-file"></a>С помощью файла Application.pkgdef  
 Включает шаблон решения изолированной оболочки *имя_решения*. Файл Application.pkgdef, который позволяет изменять следующие возможности:  
  
##### <a name="the-application-title"></a>Заголовок приложения  
 Можно настроить заголовок приложения, имя, которое отображается в заголовке окна приложения, изменив значение строки «Имя приложения» в *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Если не хотите, чтобы заголовок приложения, чтобы открыть проект, который в данный момент загружен, измените значение в строке «ShowHierarchyRootInTitle» *имя_решения*. Файл Application.pkgdef из DWORD:&00000;001 DWORD:&00000;000.  
  
##### <a name="the-application-icon"></a>Значок приложения  
 Можно изменить значок приложения, значок, которая отображается по имени приложения в строке заголовка приложения. Скопируйте в каталог значок другой значок. В **обозревателе**, добавить значок для папки с файлами ресурсов. Затем откройте файл VSShellStub.rc и замените значение IDI_STUBPROGRAM имя нового значка. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Логотип командной строки  
 Можно настроить командной строки эмблему, текст, отображаемый при запуске приложения из командной строки, изменив значение в строке «CommandLineLogo» *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Имя вложенной папки файлов пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение в строке «UserFilesSubFolderName» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Заголовок узла дерева решений в диалоговом окне Новый проект  
 Заголовок узла решения, в диалоговом окне Новый проект можно настраивать, изменяя значение в строке «NewProjDlgSlnTreeNodeTitle» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Заголовок установленных шаблонов в диалоговом окне Новый проект  
 Можно изменить заголовок установленных шаблонов в диалоговом окне Новый проект, изменив значение в строке «NewProjDlgInstalledTemplatesHdr» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Скрытие прочие файлы по умолчанию или нет  
 Можно ли скрыть прочие файлы по умолчанию путем изменения значения в строке «HideMiscellaneousFilesByDefault» *имя_решения*. Файл Application.pkgdef. Чтобы скрыть прочие файлы, установите значение `dword:00000001`, а для отображения файлов, установите значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Следует ли отключить в окне вывода  
 Можно указать, следует ли отключить, изменив значение строки «DisableOutputWindow» в окне вывода в приложении *имя_решения*. Файл Application.pkgdef. Чтобы отключить в окне вывода, установите значение `dword:00000001`и чтобы показывать окно вывода, установите значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Разрешать перенесенных файлов в главном окне или нет  
 Можно указать ли разрешить перенесенных файлов в главном окне приложения путем изменения значения в строке «AllowsDroppedFilesOnMainWindow» *имя_решения*. Файл Application.pkgdef. Чтобы разрешить удаленные файлы, установите значение `dword:00000001`и запретить перенесенных файлов, установите значение `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Страница поиска по умолчанию  
 Можно настроить страница веб-браузера, которое является страницей, отображается при открытии окна веб-обозревателя, изменив значение строки «DefaultSearchPage» в *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>Домашняя страница по умолчанию  
 Можно настроить домашнюю страницу, изменив значение в строке «DefaultHomePage» *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Скрыть основные принципы решения или нет  
 Можно указать ли скрыть решение в приложение путем изменения значения в строке «HideSolutionConcept» *имя_решения*. Файл Application.pkgdef. Чтобы скрыть решения, установите значение `dword:00000001`, чтобы показать решение, со значением `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Ядро отладки по умолчанию  
 Можно изменить модуль отладки, используемые приложением, изменив значение в строке «DefaultDebugEngine» *имя_решения*. Файл Application.pkgdef GUID своим отладчиком.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Расширение файла параметров пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение в строке «UserOptsFileExt» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Расширение файла решения  
 Можно изменить расширение, используемое для файлов решения, изменив значение в строке «SolutionFileExt» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Корня папки файлов пользователя по умолчанию  
 Можно изменить имя корневой папки файлов пользователя для приложения, изменив значение в строке «UserFilesSubFolderName» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Идентификатор создателя файла решения  
 Можно изменить идентификатор, используемый для файлов решения, изменив значение в строке «SolutionFileCreatorIdentifier» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>Расположения проектов по умолчанию  
 Имя расположения проектов по умолчанию можно изменить, изменив значение в строке «DefaultProjectsLocation» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Локализация пакета приложения  
 Можно изменить пакет локализации, который используется для вашего приложения, изменив значение в строке «AppLocalizationPackage» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Отображаемый корень иерархии в заголовке или нет  
 Можно указать ли отображаемый корень иерархии в заголовке окна в приложении, изменив значение в строке «ShowHierarchyRootInTitle» *имя_решения*. Файл Application.pkgdef. Чтобы отобразить корень иерархии, присвойте значение `dword:00000001`, чтобы скрыть корень иерархии, со значением `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Указание начальной страницы  
 Чтобы указать начальную страницу для пользовательского приложения, в *имя_решения*. Файл Application.pkgdef присвоено значение «DisableStartPage» `dword:00000000`и в разделе `[$RootKey$\StartPage\Default]` значение URI расположение XAML-файл:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 В файле Applicationcommands.vsct в *имя_решения*проект пользовательского интерфейса, закомментируйте запись «No_ShellPkg_startPageCommand»:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Необходимо добавить XAML-файл и любые графические файлы, необходимо, для *имя_решения* проекта. На самом деле эти файлы должны копироваться в *имя_решения* в каталоге проекта не добавлены из некоторых других каталогов.  
  
 Для всех файлов, установите **тип элемента** свойства **изолированной оболочки файловой** в порядке для файлов для копирования *$RootFolder$* каталога. (Чтобы задать **тип элемента** свойства, щелкните правой кнопкой мыши файл и выберите **свойства**. Это свойство находится в разделе **свойства конфигурации**, **Общие**.)  
  
 Дополнительные сведения о настройке начальные страницы в разделе [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>С помощью других элементов изолированной оболочки  
 Можно использовать другие файлы и проекты, которые включены в шаблоне решения изолированной оболочки для дальнейшей настройки приложения.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Включение или отключение пакетов Visual Studio  
 *Имя_решения*.pkgundef файл позволяет отключить определенные виды функциональных возможностей Visual Studio, за исключением определенных пакетов. Например следующую строку:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Удаляет из набора шаблонов проектов, которые отображаются в проект прочие файлы **новый проект** диалогового окна. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Включение или отключение команды меню  
 *Имя_решения*UI.vsct файл содержит список закомментированных все команды меню, доступные для изолированной оболочки. Чтобы отключить данной команды, раскомментируйте соответствующую строку. Например, чтобы отключить разделения окна и комментарий, раскомментируйте `<Define name="No_SplitCommand"/>` строки. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Битовая карта, используемая на экране-заставке  
 Битовая карта, используемая на экране-заставке называется окно, которое отображается при запуске приложения, изменив значение в строке «SplashScreenBitmap» можно настроить *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Справка о программе "окна"  
 В шаблоне изолированной оболочки имеется отдельный проект, который можно использовать для настройки справки или "о программе" для вашего приложения. Дополнительные сведения см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
