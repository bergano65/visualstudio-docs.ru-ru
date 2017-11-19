---
redirect_url: shell/customizing-the-isolated-shell
title: "Настройка изолированной оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35aab40dbacd814dcec281ff1f3dd529b29d4424
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-isolated-shell"></a>Настройка изолированной оболочки
Приложения Visual Studio изолированной оболочки можно настроить, изменив различных аспектов пользовательского интерфейса Visual Studio и путем ограничения команд и функций, включенных в специализированные приложения.  
  
## <a name="using-the-applicationpkgdef-file"></a>С помощью файла Application.pkgdef  
 Шаблонное решение изолированной оболочки включает *имя_решения*. Файл Application.pkgdef, который позволяет изменять следующие возможности:  
  
##### <a name="the-application-title"></a>Название приложения  
 Вы можете настроить заголовок приложения, имя, которое отображается в заголовке окна приложения, путем изменения значения в строке «Имя_приложения» *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Если заголовок приложения для отображения проект, который в данный момент загружен не требуется, измените значение в строке «ShowHierarchyRootInTitle» *имя_решения*. Файл Application.pkgdef из DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Значок приложения  
 Вы можете настроить значок приложения, который является значок, отображаемый в заголовке окна приложения имя приложения. Скопируйте в каталог значок другой значок. В **обозревателе решений**, добавить значок для папки с файлами ресурсов. Затем откройте файл VSShellStub.rc и замените значение IDI_STUBPROGRAM имя нового значка. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Логотип командной строки  
 Можно настроить командной строки логотипом — текст, который появляется, когда приложение запускается из командной строки, путем изменения значения в строке «CommandLineLogo» *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Имя вложенной папки файлов пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение в строке «UserFilesSubFolderName» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Заголовок узла дерева решения в диалоговое окно нового проекта  
 Заголовок узла решения в диалоговое окно нового проекта можно настраивать, изменяя значение строки «NewProjDlgSlnTreeNodeTitle» в *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Заголовок установленных шаблонов в диалоговое окно нового проекта  
 Заголовок установленных шаблонов в диалоговое окно нового проекта можно изменить, изменив значение в строке «NewProjDlgInstalledTemplatesHdr» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Скрытие различных файлов по умолчанию или нет  
 Можно указать необходимость скрыть прочие файлы по умолчанию путем изменения значения в строке «HideMiscellaneousFilesByDefault» *имя_решения*. Файл Application.pkgdef. Чтобы скрыть прочие файлы, задайте значение `dword:00000001`и для отображения файлов, установите значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Следует ли отключить в окне вывода  
 Можно указать, следует ли отключить, изменив значение строки «DisableOutputWindow» в окне вывода в приложении *имя_решения*. Файл Application.pkgdef. Чтобы отключить в окне вывода, установите значение `dword:00000001`и для отображения в окне вывода, установите значение `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Разрешение удаленных файлов в главном окне или нет  
 Можно указать ли разрешение удаленных файлов в главном окне приложения путем изменения значения в строке «AllowsDroppedFilesOnMainWindow» *имя_решения*. Файл Application.pkgdef. Чтобы разрешить удаленные файлы, задайте значение `dword:00000001`и для запрещения удаленных файлов, установите значение `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Страница поиска по умолчанию  
 Можно настроить странице браузера веб-страница, отображаемая при открытии окна веб-обозревателя, изменив значение в строке «DefaultSearchPage» является *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>Домашняя страница по умолчанию  
 На домашней странице можно настраивать, изменяя значение строки «DefaultHomePage» в *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Скрыть основные принципы решения или нет  
 Можно указать необходимость скрыть решения в приложении, изменив значение строки «HideSolutionConcept» в *имя_решения*. Файл Application.pkgdef. Чтобы скрыть решения, задайте значение `dword:00000001`и для отображения решения, установите значение `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Модуль отладки по умолчанию  
 Вы можете изменить модуль отладки, используемые приложением, изменив значение в строке «DefaultDebugEngine» *имя_решения*. Файл Application.pkgdef идентификатор GUID для вашего модуля отладки.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Расширение файла параметров пользователя  
 Можно изменить имя папки, приложение сохраняет пользовательских файлов, изменив значение в строке «UserOptsFileExt» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Расширение файла решения  
 Можно изменить модуль, используемый для файлов решения, изменив значение в строке «SolutionFileExt» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Корневая папка файлов пользователей по умолчанию  
 Можно изменить имя корневой папки файлов пользователей для вашего приложения, изменив значение в строке «UserFilesSubFolderName» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Идентификатор создателя файла решения  
 Можно изменить идентификатор, используемый для файлов решения, изменив значение в строке «SolutionFileCreatorIdentifier» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>Расположения проектов по умолчанию  
 Имя расположения проектов по умолчанию можно изменить, изменив значение в строке «DefaultProjectsLocation» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Локализация пакета приложения  
 Можно изменить локализации пакета, который используется для вашего приложения, путем изменения значения в строке «AppLocalizationPackage» *имя_решения*. Файл Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Показать основание иерархии в заголовке или нет  
 Можно включить или отключить для отображения корня иерархии в заголовке окна в приложении, изменив значение строки «ShowHierarchyRootInTitle» в *имя_решения*. Файл Application.pkgdef. Чтобы отобразить корень иерархии, присвойте значение `dword:00000001`, чтобы скрыть корень иерархии, со значением `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Указание начальной страницы  
 Чтобы указать начальную страницу для вашего приложения, в *имя_решения*. Файл Application.pkgdef присвоено значение «DisableStartPage» `dword:00000000`и в разделе `[$RootKey$\StartPage\Default]` задано расположение файла .xaml URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 В файле Applicationcommands.vsct в *имя_решения*проекта пользовательского интерфейса, закомментируйте запись «No_ShellPkg_startPageCommand»:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Необходимо добавить XAML-файл и любые графические файлы, необходимо, с *имя_решения* проекта. Эти файлы должны копироваться фактически в *имя_решения* каталога проекта, не добавлены из некоторых других каталогов.  
  
 Для всех файлов, задайте **тип элемента** свойства **изолированной оболочки файлов** в порядке для файлов для копирования *$RootFolder$* каталога. (Чтобы задать **тип элемента** свойства, щелкните правой кнопкой мыши файл и выберите **свойства**. Это свойство находится в папке **свойства конфигурации**, **Общие**.)  
  
 Дополнительные сведения о настройке начальных страниц см. в разделе [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>С помощью других элементов изолированной оболочки  
 Можно использовать другие файлы и проекты, которые включены в шаблон решения изолированной оболочки для дальнейшей настройки приложения.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Включение и отключение пакетов Visual Studio  
 *Имя_решения*.pkgundef файл позволяет отключить некоторые функциональные возможности Visual Studio, за исключением определенных пакетов. Например введите следующую строку:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Удаляет из набора шаблонов проектов, отображаемых в проект прочие файлы **новый проект** диалогового окна. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Включение и отключение команд меню  
 *Имя_решения*UI.vsct файл содержит список всех команд меню, доступных для изолированной оболочки комментарий. Чтобы отключить данной команды, раскомментируйте соответствующей строки. Например, чтобы отключить комментария/разделения окна, раскомментируйте `<Define name="No_SplitCommand"/>` строки. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Битовая карта, используемая на экране-заставке  
 Вы можете настроить Битовая карта, используемая на экране-заставке, — это окно, которое отображается при запуске приложения, изменив значение строки «SplashScreenBitmap» в *имя_решения*. Файл Application.pkgdef. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Справку о программе "окна"  
 В шаблоне изолированной оболочки имеется отдельный проект, можно использовать для настройки Справка / "о программе" для вашего приложения. Дополнительные сведения см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).