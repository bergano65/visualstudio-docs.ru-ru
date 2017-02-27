---
title: "Регистрация типа проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проекты [Visual Studio SDK] новый проект записи реестра"
  - "реестр, новых типов проектов"
  - "Регистрация новых типов проектов"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Регистрация типа проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При создании нового типа проекта, необходимо создать записей реестра, которые позволяют [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] определить и работать с системным типом проекта.  Как правило, создаются эти записи реестра с помощью файла сценария реестра \(.rgs\).  
  
 В примере, приведенном ниже, выписки из реестра предоставляют пути по умолчанию, и данные, где применимо, выполните таблицей, содержащей записи из сценария реестра для каждой выписки.  Таблицы содержат записи и дополнительные сведения о выписках скрипта.  
  
> [!NOTE]
>  Следующие данные реестра предназначены примере типа и назначений записей в скриптах реестра будет записывать для регистрации тип проекта.  В фактических записи и их используют могут отличаться в зависимости от конкретных требований конкретного типа проекта.  Необходимо просмотреть образцы, доступные для нахождения, во многом напоминает тип проекта разрабатывается и затем проанализировать скрипт реестра для этого образца.  
  
 В следующих примерах из HKEY\_CLASSES\_ROOT.  
  
## Пример  
  
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
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@`|REG\_SZ|`FigPrjFile`|Имя и описание файлов типа проекта, имеющие расширения .figp.|  
|`Content Type`|REG\_SZ|`Text/plain`|Тип содержимого для файлов проекта.|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|По умолчанию значок, используемый для проекта этого типа.  Оператор %MODULE% завершена в реестре к обычному размещению библиотеки DLL типа проекта.|  
|`@`|REG\_SZ|`&Open in Visual Studio`|По умолчанию приложение, в котором будет открыт этот тип проекта.|  
|`@`|REG\_SZ|`devenv.exe "%1"`|По умолчанию команда, которая будет открыт проект выполняется при получении этого типа.|  
  
 В следующих примерах из HKEY\_LOCAL\_MACHINE и находятся в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 99.0Exp \\ пакетами\].  
  
## Пример  
  
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
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@` \(По умолчанию\)|REG\_SZ|`FigPrj Project VSPackage`|Локализуемое имя зарегистрированного VSPackage \(типа проекта\).|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|Путь к библиотеке DLL типа проекта.  Интегрированная среда разработки загружает эта библиотека DLL и передает идентификатор CLSID в VSPackage `DllGetClassObject` доступ  <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> построение  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> объект.|  
|`CompanyName`|REG\_SZ|`Microsoft`|Имя компании, начала тип проекта.|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|Имя типа проекта.|  
|`ProductVersion`|REG\_SZ|`9.0`|Номер версии выпуска типа проекта.|  
|`MinEdition`|REG\_SZ|`professional`|Выпуск, регистрированными VSPackage.|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Ключ загрузки пакета для проекта VSPackage.  Ключ проверяется при загрузке проекта после того, как среда запущена.|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|Имя файла спутникового библиотека DLL, которая содержит локализованные ресурсы для типа проекта.|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|Путь спутникового библиотеки DLL.|  
|`FigProjectsEvents`|REG\_SZ|См. раздел выписку для значения.|Задает текстовую строку, возвращаемую для этого события автоматизации.|  
|`FigProjectItemsEvents`|REG\_SZ|См. раздел выписку для значения.|Задает текстовую строку, возвращаемую для этого события автоматизации.|  
  
 Все следующие примеры находятся в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ проектами\].  
  
## Пример  
  
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
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@`|REG\_SZ|`FigPrj Project`|Имя по умолчанию проектов этого типа.|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|Идентификатор ресурса имени, извлекаемого из спутникового DLL, зарегистрированного с пакетами.|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного в VSPackage пакетами.|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|По умолчанию путь к файлам шаблонов проекта.  Эти файлы отображаются новым шаблоном проекта.|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|По умолчанию путь к файлам шаблонов элементов проекта.  Эти файлы, указанные шаблоном добавление нового элемента.|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Позволяет среде разработки для предоставления **Открыть** диалоговое окно.|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|Используется средой разработки, чтобы определить, что открываемый проект обрабатывается данным типом проекта \(фабрикой проекта\).  Формат для более чем одной записи список разделенных точкой с запятой.  Например, "vdproj; vdp".|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|Используется средой разработки, как расширение имени файла по умолчанию для операции сохранить как.|  
|`Filter Settings`|REG\_DWORD|Разные см. в разделе выписки и комментарии после таблицы.|Эти параметры используются, чтобы задать различные фильтры для отображения файлов в диалоговых окнах пользовательского интерфейса.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Идентификатор ресурса для добавляет шаблоны элементов.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь элементов проектов, перечисленных в диалоговом окне, **Добавление нового элемента** шаблон.|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Указывает порядок сортировки в узле дерева файлов, отображаемых в **Добавление нового элемента** диалоговое окно.|  
  
 В следующей таблице перечислены параметры, доступные в предыдущем фильтров сегменте кода.  
  
|Параметр фильтра|Описание|  
|----------------------|--------------|  
|`CommonFindFilesFilter`|Указывает, что один из распространенных фильтров в фильтр **Найти в файлах** диалоговое окно.  Общие фильтры, перечислены в списке фильтра перед фильтрами не маркированными как общее.|  
|`CommonOpenFilesFilter`|Указывает, что один из распространенных фильтров в фильтр **Открыть файл** диалоговое окно.  Общие фильтры, перечислены в списке фильтра перед фильтрами не маркированными как общее.|  
|`FindInFilesFilter`|Указывает, что фильтр будет одним из фильтров в **Найти в файлах** диалоговое окно и будет приведено после распространенных фильтров.|  
|`NotOpenFileFilter`|Указывает, что фильтр не будет использоваться в **Открыть файл** диалоговое окно.|  
|`NotAddExistingItemFilter`|Указывает, что фильтр не будет использоваться в поле добавить **Существующий элемент** диалоговое окно.|  
  
 По умолчанию, если фильтр не содержит один или несколько из этих флагов, то фильтр используется в **Добавление существующего элемента** диалоговое окно и  **Открыть файл** откроется диалоговое окно выберите распространенных фильтров отображается.  Фильтр не используется в **Найти в файлах** диалоговое окно.  
  
 Все следующие примеры находятся в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ проектами\].  
  
## Пример  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Идентификатор ресурса для новых шаблонов проектов.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|По умолчанию путь для проектов зарегистрированного типа проекта.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Задает порядок сортировки проектов, перечисленных в диалоговом окне мастера проектов.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 указывает на то, что проекты данного типа отображаются только в диалоговом окне новый проект.|  
  
 Все следующие примеры находятся в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ проектами\].  
  
## Пример  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@`|REG\_SZ|None|Значение по умолчанию указывает на то, что следующие записи для прочих файлов проектов записи.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для файлов шаблонов добавить новые элементы.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|По умолчанию путь элементов, которые будут отображаться в **Добавление нового элемента** диалоговое окно.|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Задает порядок сортировки для отображения в узле дерева **Добавление нового элемента** диалоговое окно.|  
  
 В следующем примере найден в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ меню\].  
  
## Пример  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Точки входа меню интегрированная среда разработки к ресурсу, использованный для извлечения сведений о меню.  Когда эти данные будут объединены в базу данных, меню, один и тот же ключ будет добавлен в разделе MenusMerged реестра.  VSPackage ничего не должен изменять непосредственно под разделом MenusMerged.  в поле данных в следующей таблице, 3 запятая\-отделять\-поля.  Первое поле указывает полный путь к файлу ресурсов меню:  
  
-   Если первое поле пропущено, то ресурс меню загружен из спутникового библиотеки DLL заданного GUID VSPackage.  
  
 Второе поле указывает идентификатор ресурса меню типа CTMENU:  
  
-   Если указан идентификатор ресурса и путь к файлу указан первым параметром, ресурс меню загружен из полного пути к файлу.  
  
-   Если идентификатор ресурса предоставлено, но путь к файлу отсутствует, ресурс меню загружен из спутникового библиотеки DLL.  
  
-   Если полный путь к файлу указан и идентификатор ресурса не указан, то предполагается, что файл, загружаемый файл настройки по порядку.  
  
 Последнее поле указывает номер версии для ресурса CTMENU.  Можно снова путем слияния меню изменить номер версии.  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|Ресурс для получения сведений о меню.|  
  
 Все следующие примеры находятся в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ NewProjectTemplates\].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для шаблонов проекта новых диаграмм.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|По умолчанию путь нового каталога проекта.  Элементы в этом каталоге будет отображаться на **Мастер создания проектов** диалоговое окно.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Устанавливает порядок, в котором будут отображены в узле дерева проекты **Создать проект** диалоговое окно.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 указывает на то, что проекты данного типа отображаются только в **Создать проект** диалоговое окно.|  
  
 В следующем примере найден в реестре с ключом \[HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 9.0Exp \\ InstalledProducts\].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного VSPackage.|  
|`UseInterface`|REG\_DWORD|`1`|1 указывает на то, что пользовательский интерфейс будет использоваться для взаимодействия с этим проектом.  0 указывает на то, что интерфейс пользовательского интерфейса.|  
  
 Файлы The.vsz, которые управляют новые типы проектов часто содержат запись RELATIVE\_PATH.  Данный путь задается относительно пути, заданному в разделе \\ запись ProductDir типа проекта в следующем ключе установки:  
  
 HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 7.0Exp \\ setup  
  
 Например, шаблоны проектов .NET Framework предприятия добавить следующие записи реестра:  
  
 HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 7.0Exp \\ setup \\ EF \\ ProductDir \= " C:\\Program Files\\Microsoft \\ Visual Studio \\ EnterpriseFrameworks  
  
 Это означает если включить запись PROJECT\_TYPE\=EF в файле .vsz, то среда выполняется поиск файлов vsz в каталоге ProductDir указанном выше.  
  
## См. также  
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)   
 [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)