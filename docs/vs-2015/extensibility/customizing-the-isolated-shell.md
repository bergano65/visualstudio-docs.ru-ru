---
title: Настройка изолированной оболочки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097186ba43202c537bf8acbe0b47893151055c19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733785"
---
# <a name="customizing-the-isolated-shell"></a>Настройка изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Приложения Visual Studio изолированной оболочки можно настроить, изменив различных аспектов пользовательского интерфейса Visual Studio и за счет ограничения команд и функций, включенных в специализированные приложения.  
  
## <a name="using-the-applicationpkgdef-file"></a>С помощью файла Application.pkgdef  
 Включает в себя шаблон решения изолированной оболочки *SolutionName*. Application.pkgdef файл, который позволяет изменять следующие функции:  
  
##### <a name="the-application-title"></a>Заголовок приложения  
 Вы можете настроить заголовок приложения, которое является именем, отображаемый в заголовке окна приложения, изменив значение строки «AppName» в *SolutionName*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Если вы не хотите, чтобы заголовок приложения для отображения проекта, который в данный момент загружается, измените значение в строке «ShowHierarchyRootInTitle» *SolutionName*. Файл Application.pkgdef из DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Значок приложения  
 Вы можете настроить значок приложения, в которой значок, отображаемый по имени приложения в заголовке окна приложения. Скопируйте в каталог значок другой значок. В **обозревателе решений**, добавить значок для папки с файлами ресурсов. Затем откройте файл VSShellStub.rc и замените значение IDI_STUBPROGRAM именем значок "Создать". Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Логотип командной строки  
 Можно настроить логотип командной строки, который является текст, отображаемый, когда приложение запускается из командной строки, изменив значение строки «CommandLineLogo» в *SolutionName*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Имя вложенной папки файлов пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение строки «UserFilesSubFolderName» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Заголовок узла дерева решения в диалоговом окне нового проекта  
 Название узел решения в диалоговом окне нового проекта можно настраивать, изменяя значение в строке «NewProjDlgSlnTreeNodeTitle» *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Заголовок установленных шаблонов в диалоговом окне нового проекта  
 Можно изменить, изменив значение строки «NewProjDlgInstalledTemplatesHdr» в заголовке установленных шаблонов в диалоговом окне нового проекта *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Следует ли скрыть прочие файлы по умолчанию  
 Можно указать, следует ли скрыть прочие файлы по умолчанию, изменив значение строки «HideMiscellaneousFilesByDefault» в *SolutionName*. Файл Application.pkgdef. Чтобы скрыть прочие файлы, задайте значение `dword:00000001`и для отображения файлов, задайте значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Следует ли отключить в окне вывода  
 Можно указать, следует ли отключить, изменив значение строки «DisableOutputWindow» в окне вывода в приложении *SolutionName*. Файл Application.pkgdef. Чтобы отключить в окне вывода, установите значение `dword:00000001`и чтобы показывать окно вывода, задайте значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Следует ли разрешить перенесенных файлов в главном окне  
 Можно указать, следует ли разрешить перенесенных файлов в главное окно приложения, изменив значение строки «AllowsDroppedFilesOnMainWindow» в *SolutionName*. Файл Application.pkgdef. Чтобы разрешить перенесенных файлов, задайте значение `dword:00000001`и запретить перенесенных файлов, задайте значение `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>На странице поиска по умолчанию  
 Можно настроить веб-страницы браузера, который является страницей, которое отображается при открытии окна веб-обозревателя, изменив значение строки «DefaultSearchPage» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>Домашняя страница по умолчанию  
 На домашней странице можно настраивать, изменяя значение в строке «DefaultHomePage» *SolutionName*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Следует ли скрыть основные принципы решения  
 Можно указать необходимость скрыть решения в приложении, изменив значение строки «HideSolutionConcept» в *SolutionName*. Файл Application.pkgdef. Чтобы скрыть решения, задайте значение `dword:00000001`и чтобы отобразить решения, задайте значение `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Модуль отладки по умолчанию  
 Можно изменить модуль отладки, используемые приложением, изменив значение строки «DefaultDebugEngine» в *SolutionName*. Файл Application.pkgdef идентификатор GUID вашего модуля отладки.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Расширение файла параметров пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение строки «UserOptsFileExt» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Расширение файла решения  
 Можно изменить расширение, используемое для файлов решения, изменив значение строки «SolutionFileExt» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Корневой папки файлов пользователя по умолчанию  
 Имя корневой папки файлов пользователей для приложения можно изменить, изменив значение строки «UserFilesSubFolderName» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Идентификатор создателя файла решения  
 Можно изменить идентификатор, используемый для файлов решения, изменив значение строки «SolutionFileCreatorIdentifier» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>Размещение проектов по умолчанию  
 Имя расположения проектов по умолчанию можно изменить, изменив значение строки «DefaultProjectsLocation» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Пакет локализации приложения  
 Можно изменить пакет локализации, используемый для вашего приложения, изменив значение строки «AppLocalizationPackage» в *SolutionName*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Показать основание иерархии в заголовке или нет  
 Можно указать ли Показать корня иерархии в заголовке окна в приложении, изменив значение строки «ShowHierarchyRootInTitle» в *SolutionName*. Файл Application.pkgdef. Чтобы отобразить корня иерархии, задайте значение `dword:00000001`и чтобы скрыть корень иерархии, задайте значение `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Задание начальной страницы  
 Чтобы указать начальную страницу для пользовательского приложения, в *SolutionName*. Файл Application.pkgdef присвоено значение «DisableStartPage» `dword:00000000`и в разделе `[$RootKey$\StartPage\Default]` значение URI расположение XAML-файл:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 В файле Applicationcommands.vsct *SolutionName*проекта пользовательского интерфейса, закомментируйте элемент «No_ShellPkg_startPageCommand»:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 XAML-файл, а нужные файлы рисунков, вам требуется, необходимо добавить *SolutionName* проекта. Фактически эти файлы необходимо скопировать для *SolutionName* каталог проекта, не добавлены из некоторых других каталога.  
  
 Для всех файлов, задайте **тип элемента** свойства **изолированной оболочки файловой** в порядке для файлов для копирования *$RootFolder$* каталога. (Чтобы задать **тип элемента** свойство, щелкните правой кнопкой мыши файл и выберите **свойства**. Это свойство можно найти в разделе **свойства конфигурации**, **Общие**.)  
  
 Дополнительные сведения о настройке начальных страницах см. в разделе [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>С помощью других элементов изолированной оболочки  
 Можно использовать другие файлы и проекты, включенные в шаблоне решения изолированной оболочки для дальнейшей настройки приложения.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Включение или отключение пакетов Visual Studio  
 *SolutionName*файла .pkgundef позволяет отключить определенные виды функциональных возможностей Visual Studio, за исключением определенных пакетов. Например введите следующую строку:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Удаляет из набора шаблонов проектов, в проект прочих файлов **новый проект** диалоговое окно. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Включение и отключение команд меню  
 *SolutionName*UI.vsct файл включает закомментированных список всех команд меню, доступных для изолированной оболочки. Чтобы отключить определенной команды, раскомментируйте соответствующей строки. Например, чтобы отключить комментарий Window/Split, раскомментируйте `<Define name="No_SplitCommand"/>` строки. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Битовая карта, используемая на экран-заставка  
 Вы можете настроить растровое изображение, используемое на заставки, которая является окном, которое отображается при запуске приложения, изменив значение строки «SplashScreenBitmap» в *SolutionName*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Справка/о окна  
 В шаблоне изолированной оболочки имеется отдельный проект, можно использовать для настройки справки / "о программе" для вашего приложения. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).

