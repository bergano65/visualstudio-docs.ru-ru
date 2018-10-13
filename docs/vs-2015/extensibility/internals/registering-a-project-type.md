---
title: Регистрация типа проекта | Документация Майкрософт
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
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30956d812aa2ece166231d6ae7580b226025e308
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271782"
---
# <a name="registering-a-project-type"></a>Регистрация типа проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При создании нового типа проекта, необходимо создать записи реестра, которые позволяют [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для распознавания и работать с типом проекта. Обычно создают эти записи реестра с помощью файла сценария (.rgs) реестра.  
  
 В следующем примере операторы из реестра укажите пути по умолчанию и данных там, где это применимо, а затем таблицу, которая содержит элементы из скрипта реестра для каждой инструкции. Таблицы содержат записи скрипта и Дополнительные сведения об инструкциях.  
  
> [!NOTE]
>  Следующие сведения реестра предназначен пример типа и целей записей в реестре сценарии, которые можно будет записывать для регистрации типа проекта. Фактические записи и их использование может отличаться в зависимости от определенных требований типа проекта. Ознакомьтесь с примерами, доступные для поиска, сильно напоминает типа разрабатываемого проекта и просмотрите скрипт реестра для данного примера.  
  
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
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Имя и описание типа файлов проекта, которые имеют расширение .figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Тип содержимого для файлов проекта.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Значок по умолчанию, используемый для проекта этого типа. Оператор % MODULE % завершено в реестре в расположение по умолчанию для типа проекта библиотеки DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Приложение по умолчанию, в котором будет открыт этим типом проектов.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Команда по умолчанию, которая будет запускаться при открытии проекта данного типа.|  
  
 В следующих примерах из HKEY_LOCAL_MACHINE и находятся в реестре в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
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
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@` (По умолчанию)|REG_SZ|`FigPrj Project VSPackage`|Это локализуемые имя зарегистрировано VSPackage (типа проекта).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Путь к типу проекта библиотеки DLL. Загружает эту библиотеку DLL интегрированной среды разработки и передает VSPackage CLSID для `DllGetClassObject` для получения <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> для создания <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> объекта.|  
|`CompanyName`|REG_SZ|`Microsoft`|Имя компании, разработавшей типа проекта.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Имя для типа проекта.|  
|`ProductVersion`|REG_SZ|`9.0`|Номер версии типа проекта release.|  
|`MinEdition`|REG_SZ|`professional`|Выпуск пакета VSPackage зарегистрирован.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Пакет загружается ключ для проекта VSPackage. Ключ проверяется при загрузке проекта, после запуска среды.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Имя файла вспомогательной библиотеки DLL, которая содержит локализованные ресурсы для типа проекта.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Путь к вспомогательной библиотеке DLL.|  
|`FigProjectsEvents`|REG_SZ|См. инструкции для значения.|Определяет текстовую строку, возвращаемые для этого события автоматизации.|  
|`FigProjectItemsEvents`|REG_SZ|См. инструкции для значения.|Определяет текстовую строку, возвращаемые для этого события автоматизации.|  
  
 Все следующие примеры расположены в реестре в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Имя по умолчанию для проектов этого типа.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Идентификатор ресурса имени должно быть извлечено из вспомогательной библиотеки DLL зарегистрирован в пакеты.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса VSPackage зарегистрирован в пакеты.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию для файлов шаблона проекта. Это файлы, отображаемые шаблон нового проекта.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|По умолчанию путь к файлам шаблона элемента проекта. Это файлы, отображаться шаблоном Добавление нового элемента.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Включает интегрированную среду разработки для реализации **откройте** диалоговое окно.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Используется для определения того, обрабатывается ли этим типом проектов (фабрики проектов) открываемого проекта интегрированной среды разработки. Формат для более чем одной записи представляет собой список разделенных точками с запятой. Например «vdproj; vdp».|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Использовать в интегрированной среде разработки как расширение имени файла по умолчанию для операции Сохранить как.|  
|`Filter Settings`|REG_DWORD|Различные, см. в разделе инструкций и комментариев, в следующей таблице.|Эти параметры используются для настройки различных фильтров для отображения файлов в диалоговых окнах пользовательского интерфейса.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Идентификатор ресурса для шаблонов добавить элемент.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь проекта элементов, отображаемых в диалоговом окне для **Добавление нового элемента** шаблона.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Определяет порядок сортировки в узле дерева файлов, отображаемых в **Добавление нового элемента** диалоговое окно.|  
  
 Ниже приведены параметры фильтры, доступные в предыдущем фрагменте кода.  
  
|Параметр фильтра|Описание|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Указывает, что фильтр является одним из распространенных фильтров в **поиск в файлах** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, которые не помечены как распространенные.|  
|`CommonOpenFilesFilter`|Указывает, что фильтр является одним из распространенных фильтров в **открыть файл** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, которые не помечены как распространенные.|  
|`FindInFilesFilter`|Указывает, что фильтр будет один из фильтров в **поиск в файлах** диалогового окна поле и приводятся после распространенных фильтров.|  
|`NotOpenFileFilter`|Указывает, что фильтр не будет использоваться в **открыть файл** диалоговое окно.|  
|`NotAddExistingItemFilter`|Указывает, что фильтр не будет использоваться в Add **существующий элемент** диалоговое окно.|  
  
 По умолчанию, если фильтр отсутствует один или несколько из следующих флагов набора, фильтр используется в **добавить существующий элемент** диалоговое окно и **открыть файл** диалоговое окно после перечислены общие фильтры. Фильтр не используется в **поиск в файлах** диалоговое окно.  
  
 Все следующие примеры расположены в реестре в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Пример  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Идентификатор ресурса для шаблоны новых проектов.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь для проектов типа зарегистрированных проекта по умолчанию.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Задает порядок проекты отображаются в окне мастера новых проектов сортировки.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 указывает, что проекты этого типа отображаются только в диалоговом окне нового проекта.|  
  
 Все следующие примеры расположены в реестре в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Нет|Значение по умолчанию, который указывает, что следующие записи в операциях, прочие файлы проектов.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для файлов шаблонов Добавление новых элементов.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|По умолчанию путь к элементам, которые будут отображаться в **Добавление нового элемента** диалоговое окно.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Устанавливает порядок сортировки для отображения в узле дерева **Добавление нового элемента** диалоговое окно.|  
  
 Следующий пример находится в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] реестра.  
  
## <a name="example"></a>Пример  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Запись меню указывает на ресурс, используемого для получения сведений меню интегрированной среды разработки. При слиянии эти данные в базу данных меню в разделе MenusMerged реестра будут добавляться тот же ключ. Пакет VSPackage не следует изменять что-то в разделе MenusMerged напрямую. В поле данных в таблице ниже существуют три разделителями запятыми поля. Первое поле определяет полный путь файла ресурсов меню:  
  
-   Если первое поле указан, ресурс загружается из вспомогательной библиотеки DLL, определяемом по GUID пакета VSPackage.  
  
 Второе поле указывает идентификатор ресурса меню типа CTMENU:  
  
-   Если указан идентификатор ресурса, и путь к файлу предоставляется первый параметр, ресурс меню загружается из полный путь к файлу.  
  
-   Путь к файлу не указан идентификатор ресурса, ресурс загружается из вспомогательной библиотеки DLL.  
  
-   Если указан полный путь к файлу, а указан идентификатор ресурса, к загружаемому файлу ожидается должен быть файлом, руководитель технологического ОТДЕЛА компании.  
  
 Последнее поле соответствует номеру версии для ресурса CTMENU. Чтобы объединить меню снова, изменение номера версии.  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|Ресурс, чтобы получить сведения о меню.|  
  
 Все следующие примеры расположены в реестре в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для шаблонов фигур проект новый проект.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|По умолчанию путь к каталогу новых проектов. Элементы в этом каталоге будут отображены в **мастера создания проекта** диалоговое окно.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Задает порядок, в котором проектов будет отображаться в узле дерева **новый проект** диалоговое окно.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 означает, что проекты этого типа отображаются только в **новый проект** диалоговое окно.|  
  
 Следующий пример находится в разделе [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] реестра.  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного пакета VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 указывает, что пользовательский Интерфейс будет использоваться для взаимодействия с этим проектом. 0 указывает, что не существует пользовательского интерфейса.|  
  
 The.vsz файлы, определяющие новых типов проектов, часто содержат записи устанавливается. Этот путь задается относительно пути, указанные в разделе \ProductDir запись типа проекта в следующий раздел установки:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Например шаблоны проектов Enterprise Frameworks добавьте следующие записи реестра:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Это означает, что если вы включите PROJECT_TYPE = entry EF в VSZ-файле, находит среды, ваши .vsz файлы в каталоге ProductDir, указанном ранее.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список: Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)   
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

