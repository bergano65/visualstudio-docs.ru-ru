---
title: Регистрация типа проекта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705874"
---
# <a name="registering-a-project-type"></a>Регистрация типа проекта
При создании нового типа проекта необходимо создавать записи [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] реестра, которые позволяют распознавать и работать с типом проекта. Обычно эти записи реестра создаются с помощью файла скрипта реестра (.rgs).

 В приведенном ниже примере заявления из реестра предоставляют пути по умолчанию и данные, где это применимо, а затем таблицу, содержащую записи из сценария реестра для каждой выписки. Таблицы предоставляют записи сценариев и дополнительную информацию о заявлениях.

> [!NOTE]
> Следующая информация реестра предназначена для примера типа и целей записей в реестра скриптов вы будете писать, чтобы зарегистрировать свой тип проекта. Ваши фактические записи и их использование могут варьироваться в зависимости от конкретных требований типа проекта. Вы должны просмотреть образцы, доступные, чтобы найти тот, который очень похож на тип проекта, который вы разрабатываете, а затем просмотреть сценарий реестра для этого образца.

 Следующие примеры из HKEY_CLASSES_ROOT.

## <a name="example"></a>Пример

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Имя и описание файлов типа проекта, которые имеют расширение .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Тип содержимого для файлов проекта.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Значок по умолчанию, используемый для проекта этого типа. Выписка %MODULE% завершается в реестре к местоположению по умолчанию типа проекта DLL.|
|`@`|REG_SZ|`&Open in Visual Studio`|Приложение по умолчанию, в котором будет открыт этот тип проекта.|
|`@`|REG_SZ|`devenv.exe "%1"`|Команда по умолчанию, которая будет запущена при открытии проекта этого типа.|

 Следующие примеры относятся к HKEY_LOCAL_MACHINE и находятся в реестре под ключом «HKEY_LOCAL_MACHINE»-ПРОГРАММА»Microsoft-VisualStudio »99.0Exp »Пакеты».

## <a name="example"></a>Пример

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@` (по умолчанию)|REG_SZ|`FigPrj Project VSPackage`|Локализованное название этого зарегистрированного VSPackage (тип проекта).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Путь типа проекта DLL. IDE загружает этот DLL и передает `DllGetClassObject` VSPackage CLSID, чтобы добраться <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> до строительства <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> объекта.|
|`CompanyName`|REG_SZ|`Microsoft`|Название компании, которая разработала тип проекта.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Название для типа проекта.|
|`ProductVersion`|REG_SZ|`9.0`|Номер версии выпуска типа проекта.|
|`MinEdition`|REG_SZ|`professional`|Издание VSPackage регистрируется.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Ключ загрузки пакета для проекта VSPackage. Ключ проверяется при загрузке проекта после запуска среды.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Название файла спутника DLL, содержащего локализованные ресурсы для типа проекта.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Путь спутника DLL.|
|`FigProjectsEvents`|REG_SZ|Просчитайте заявление о значении.|Определяет строку текста, возвращенную для этого события автоматизации.|
|`FigProjectItemsEvents`|REG_SZ|Просчитайте заявление о значении.|Определяет строку текста, возвращенную для этого события автоматизации.|

 Все следующие примеры находятся в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio»9.0Exp».

## <a name="example"></a>Пример

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|По умолчанию название проектов этого типа.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Идентификатор ресурса имени, которое будет получено со спутника DLL, зарегистрированного в рамках пакетов.|
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса VSPackage, зарегистрированный в пакетах.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию файлов шаблона проекта. Это файлы, отображаемые шаблоном New Project.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Путь по умолчанию файлов шаблона элемента проекта. Это файлы, отображаемые шаблоном Добавить новый элемент.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Позволяет IDE реализовать **открытый диалоговый** ящик.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Используется IDE для определения того, обрабатывается ли открываемый проект этим типом проекта (фабрика проекта). Формат для более чем одной записи представляет собой список делимитированных запятых. Например, "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Используется IDE в качестве расширения имени файла по умолчанию для операции «Сохранить как».|
|`Filter Settings`|REG_DWORD|Различные, увидеть заявления и комментарии после таблицы.|Эти настройки используются для установки различных фильтров для отображения файлов в диалоговых коробках UI.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Идентификатор ресурсов для шаблонов Добавления пункта.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь элементов проекта, отображаемых в диалоговом поле для шаблона **Добавить новый элемент.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Определяет порядок сортировки в древесном узеле файлов, отображаемых в диалоговом поле **Add New Item.**|

 В следующей таблице показаны параметры фильтров, доступные в предыдущем сегменте кода.

|Вариант фильтра|Описание|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Указывается, что фильтр является одним из распространенных фильтров в диалоговом поле **«Найти в файлах».** Общие фильтры перечислены в списке фильтров, прежде чем фильтры не помечены как общие.|
|`CommonOpenFilesFilter`|Указывается, что фильтр является одним из распространенных фильтров в диалоговом окне **Open File.** Общие фильтры перечислены в списке фильтров, прежде чем фильтры не помечены как общие.|
|`FindInFilesFilter`|Указывает, что фильтр будет одним из фильтров в диалоговом поле **«Найти в файлах»** и будет перечислен после общих фильтров.|
|`NotOpenFileFilter`|Означает, что фильтр не будет использоваться в диалоговом окне **Open File.**|
|`NotAddExistingItemFilter`|Указывается, что фильтр не будет использоваться в диалоговом окне **добавления элемента.**|

 По умолчанию, если фильтр не имеет одного или нескольких из этих флагов, фильтр используется в диалоговом окне **Добавления и** в диалоговом окне **Open File** после перечисления общих фильтров. Фильтр не используется в диалоговом окне **Поиска в файлах.**

 Все следующие примеры находятся в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio»9.0Exp».

## <a name="example"></a>Пример

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Идентификатор ресурсов для новых шаблонов проекта.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию для проектов зарегистрированного типа проекта.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Устанавливает порядок сортировки проектов, отображаемых в поле диалога мастеров новых проектов.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 указывает на то, что проекты этого типа отображаются только в диалоговом окне нового проекта.|

 Все следующие примеры находятся в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio»9.0Exp».

## <a name="example"></a>Пример

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Отсутствуют|Значение по умолчанию, указывававо, что следующие записи для записей проектов «Разные файлы».|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Значение идентификатора ресурсов для файлов шаблонов Добавления новых элементов.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь по умолчанию элементов, которые будут отображаться в диалоговом окне **Добавления нового элемента.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Устанавливает порядок сортировки для отображения в узло дерева диалогового окна **Добавить новый элемент.**|

 Следующий пример находится в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio »9.0Exp »Меню».

## <a name="example"></a>Пример

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Вход в меню указывает IDE на ресурс, используемый для получения информации о меню. Когда эти данные будут объединены в базу данных меню, тот же ключ будет добавлен в раздел MenusMerged реестра. VSPackage не должен изменять что-либо под разделом MenusMerged напрямую. В поле данных в следующей таблице есть три запятых отдельных поля. Первое поле определяет полный путь файла ресурсов меню:

- Если первое поле опущено, ресурс меню загружается со спутника DLL, идентифицированного GUID VSPackage.

  Второе поле определяет идентификатор ресурса меню типа CTMENU:

- Если идентификатор ресурса указан, а путь файла подается по первому параметру, ресурс меню загружается из полного пути файла.

- Если идентификатор ресурса предоставлен, а путь файла не является, ресурс меню загружается со спутника DLL.

- Если предоставляется полный путь файла и опущен идентификатор ресурса, то файл, который будет загружен, должен быть файлом КТО.

  Последнее поле определяет номер версии для ресурса CTMENU. Меню можно снова объединить, изменив номер версии.

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|Ресурс для получения информации о меню.|

 Все следующие примеры находятся в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio»9.0Exp »NewProjectTemplates».

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Значение идентификатора ресурсов для шаблонов проекта «Цифры» нового проекта.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию каталога новых проектов. Элементы в этом каталоге будут отображаться в диалоговом окне **нового проекта.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Устанавливает порядок отображения проектов в древесном узло диалогового окна **нового проекта.**|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 указывает на то, что проекты этого типа отображаются только в диалоговом окне **нового проекта.**|

 Следующий пример находится в реестре под ключом «HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio »9.0Exp »Установленныепродукты».

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|name|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного VSPackage.|
|`UseInterface`|REG_DWORD|`1`|1 указывает на то, что uI будет использоваться для взаимодействия с этим проектом. 0 указывает на отсутствие интерфейса интерфейса интерфейса.|

 Файлы The.vsz, контролирующие новые типы проектов, часто содержат RELATIVE_PATH запись. Этот путь отражается от пути, указанного в входе в тип проекта ProductDir в следующем ключе настройки:

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-7.0Exp -Настройка

 Например, шаблоны проектов Enterprise Frameworks добавляют следующие записи реестра:

 HKEY_LOCAL_MACHINE »ПРОГРАММНО-Такеничная-ВизуальнаяСтудия»7.0Exp-Setup/EF-ProductDir

 Это означает, что если вы включите запись PROJECT_TYPE'EF в файл ас-Vsz, то среда находит ваши файлы .vsz в каталоге ProductDir, указанном ранее.

## <a name="see-also"></a>См. также
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)
- [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
