---
title: "Регистрация типа проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a60ac9de727e8542df7455ee331737403f6bef3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-project-type"></a>Регистрация типа проекта
Когда вы создаете новый тип проекта, необходимо создать записей реестра, которые позволяют [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] распознавать и работать с типа проекта. Обычно эти записи реестра создаются с помощью файла реестра (RGS-) сценария.  
  
 В приведенном ниже примере инструкций из реестра предоставляют пути по умолчанию и данных там, где это применимо, за которым следует таблицу, которая содержит записи из реестра скрипта для каждой инструкции. Таблицы содержат записи скрипта и Дополнительные сведения об инструкциях.  
  
> [!NOTE]
>  Пример типа и целей записей в реестре скриптов, которые можно будет осуществлять запись регистрации типа проекта предназначен в реестр следующие сведения. Фактический записей и их использование может меняться в зависимости от требований конкретного типа проекта. Просмотрите образцы можно найти одну, которая напоминает тип проекта, который вы разрабатываете и просмотрите скрипт реестра для данного примера.  
  
 В следующих примерах показаны из HKEY_CLASSES_ROOT.  
  
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
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Имя и описание типа файлов проекта, которые имеют расширение .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Тип содержимого для файлов проекта.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Значок по умолчанию, используемая для проекта этого типа. Оператор % MODULE % завершено в реестре в папке по умолчанию тип проекта DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Приложение по умолчанию, в котором будет открыт этот тип проекта.|  
|`@`|REG_SZ|`devenv.exe "%1"`|По умолчанию, которая будет выполняться при открытии проекта этого типа.|  
  
 В следующих примерах из HKEY_LOCAL_MACHINE и расположены в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] реестра.  
  
## <a name="example"></a>Пример  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
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
|----------|----------|----------|-----------------|  
|`@`(По умолчанию)|REG_SZ|`FigPrj Project VSPackage`|Локализуемое имя зарегистрировать VSPackage (типа проекта).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Путь к типу проекта библиотеки DLL. Загружает этот DLL интегрированной среды разработки и передает CLSID VSPackage для `DllGetClassObject` для получения <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> для создания <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> объекта.|  
|`CompanyName`|REG_SZ|`Microsoft`|Название компании, разработанным типа проекта.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Имя для типа проекта.|  
|`ProductVersion`|REG_SZ|`9.0`|Номер версии типа проекта выпуска.|  
|`MinEdition`|REG_SZ|`professional`|Выпуск регистрируемого VSPackage.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Пакет загрузки ключа для проекта VSPackage. Ключ проверки, если проект загружается после запуска среды.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Имя файла вспомогательной библиотеки DLL, который содержит локализованные ресурсы для данного типа проектов.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Путь к DLL-Библиотеке дополнения.|  
|`FigProjectsEvents`|REG_SZ|См. инструкции для значения.|Определяет, возвращает строку текста для этого события модели автоматизации.|  
|`FigProjectItemsEvents`|REG_SZ|См. инструкции для значения.|Определяет, возвращает строку текста для этого события модели автоматизации.|  
  
 Следующие примеры расположены в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] реестра.  
  
## <a name="example"></a>Пример  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Имя по умолчанию для проектов этого типа.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Идентификатор ресурса имени должно быть извлечено из вспомогательной библиотеки DLL зарегистрирован пакетов.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса VSPackage зарегистрирован пакетов.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию файлы шаблонов проекта. Это файлы, отображаемые с помощью шаблона новый проект.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Путь по умолчанию файлы шаблонов элемента проекта. Это файлы, отображаемые в шаблоне добавить новый элемент.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Включение интегрированной среды разработки для реализации **откройте** диалоговое окно.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Используется в интегрированной среде разработки для определения, обрабатывается ли открыть проект этого типа проекта (фабрики проектов). Формат для более чем одной операции является списком разделенных точками с запятой. Например «vdproj; vdp».|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Использовать IDE как расширение имени файла по умолчанию для операции Сохранить как.|  
|`Filter Settings`|REG_DWORD|Разных, см. инструкции и примечания, в следующей таблице.|Эти параметры используются для настройки различных фильтров для отображения файлов в диалоговых окнах пользовательского интерфейса.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Идентификатор ресурса для шаблонов добавить элемент.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь проекта элементов, отображаемых в диалоговом окне **добавить новый элемент** шаблона.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Определяет порядок сортировки в узле дерева файлов, отображаемых в **Добавление нового элемента** диалоговое окно.|  
  
 В следующей таблице показаны параметры фильтры, доступные в предыдущем фрагменте кода.  
  
|Параметр фильтра|Описание|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Указывает, что фильтр — одна из распространенных фильтров в **поиск в файлах** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, не помечен как общий.|  
|`CommonOpenFilesFilter`|Указывает, что фильтр — одна из распространенных фильтров в **открыть файл** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, не помечен как общий.|  
|`FindInFilesFilter`|Показывает, что фильтр одного из фильтров в **поиск в файлах** диалогового окна поле и приводятся после общие фильтры.|  
|`NotOpenFileFilter`|Указывает, что фильтр не будет использоваться в **открыть файл** диалоговое окно.|  
|`NotAddExistingItemFilter`|Указывает, что фильтр не будет использоваться в добавления **существующий элемент** диалоговое окно.|  
  
 По умолчанию, если фильтр содержит один или несколько из следующих флагов набора, фильтр используется в **Добавление существующего элемента** диалоговое окно и **открыть файл** диалоговое окно после перечислены общие фильтры. Фильтр не используется в **поиск в файлах** диалоговое окно.  
  
 Следующие примеры расположены в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] реестра.  
  
## <a name="example"></a>Пример  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Идентификатор ресурса для шаблонов новый проект.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь для проектов типа зарегистрированного проекта по умолчанию.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Задает порядок проекты, которые отображаются в окне мастера новых проектов сортировки.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 указывает, что проекты этого типа отображаются только в диалоговом окне нового проекта.|  
  
 Следующие примеры расположены в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] реестра.  
  
## <a name="example"></a>Пример  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Нет|Значение по умолчанию, которое показывает, что следующие записи в операциях, прочие файлы проектов.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Значение идентификатора ресурсов для файлов шаблонов Добавление новых элементов.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь по умолчанию элементов, которые будут отображаться в **Добавление нового элемента** диалоговое окно.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Устанавливает порядок сортировки для отображения в узле дерева **Добавление нового элемента** диалоговое окно.|  
  
 Следующий пример находится в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] реестра.  
  
## <a name="example"></a>Пример  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Элемент меню интегрированной среды разработки указывает на ресурс, используемый для получения сведения о меню. При слиянии данных в базу данных меню тот же ключ будет добавлена в разделе MenusMerged реестра. Пакет VSPackage не следует изменять что-либо в разделе MenusMerged напрямую. Поля данных в таблице ниже показаны три разделителями запятыми поля. Первое поле определяет полный путь файла ресурсов меню:  
  
-   Если первое поле указан, ресурс меню загружается из вспомогательной библиотеки DLL с идентификатором GUID пакета VSPackage.  
  
 Второе поле определяет идентификатор ресурса меню типа CTMENU:  
  
-   Если указан идентификатор ресурса и путь к файлу указан первым параметром, ресурс меню загружается из полный путь к файлу.  
  
-   Если указан идентификатор ресурса, но не является путь к файлу, этот ресурс загружается из вспомогательной библиотеки DLL.  
  
-   Если предоставляется полный путь к файлу, а указан идентификатор ресурса, загружаемый файл ожидается CTO-файлов.  
  
 Последнее поле определяет номер версии для ресурса CTMENU. Можно объединить меню снова путем изменения номера версии.  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|Ресурс, чтобы получить сведения о меню.|  
  
 Следующие примеры расположены в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] реестра.  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для шаблонов проектов новых фигур.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|По умолчанию путь к каталогу для новых проектов. Элементы в этом каталоге будет отображаться в **мастера создания проектов** диалоговое окно.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Устанавливает порядок, в котором проектов будет отображаться в узле дерева **новый проект** диалоговое окно.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 указывает, что отображаются только в проектах этого типа **новый проект** диалоговое окно.|  
  
 Следующий пример находится в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] реестра.  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 указывает, что пользовательский Интерфейс будет использоваться для взаимодействия с этим проектом. 0 указывает, что пользовательского интерфейса, не существует.|  
  
 The.vsz файлы, которые управляют новых типов проектов часто содержит операции RELATIVE_PATH. Данный путь задается относительно пути, указанные в разделе \ProductDir запись типа проекта в следующий раздел установки:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Например шаблоны проектов Enterprise Frameworks добавьте следующие параметры реестра:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Это означает, что если вы включите PROJECT_TYPE = EF запись в файле .vsz находит среды, ваш .vsz файлы в каталоге ProductDir, указанном ранее.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)   
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)