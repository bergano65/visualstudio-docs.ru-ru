---
title: Задача MT | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e4298fa9482674232dea2cae98bb25ba51be30
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219878"
---
# <a name="mt-task"></a>MT - задача
Создает программу-оболочку для инструмента манифеста Майкрософт *(mt.exe)*. Дополнительные сведения см. в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).  
  
## <a name="parameters"></a>Параметры  
 В представленной ниже таблице приводятся параметры задачи **MT**. Большинство параметров задачи и некоторые наборы параметров соответствуют параметрам командной строки.  
  
> [!NOTE]
>  В документации *mt.exe* в качестве префикса для параметров командной строки используется дефис (**-**), но в этом разделе используется косая черта (**/**). Допустим любой префикс.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Необязательный параметр типа **String[]**.<br /><br /> Задает имя одного или нескольких файлов манифеста.<br /><br /> Дополнительные сведения см. в описании параметра **/manifest** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**AdditionalOptions**|Необязательный параметр типа **String**.<br /><br /> Список параметров командной строки. Например, /\<параметр1> /\<параметр2> /\<параметр#>. Этот параметр используется для указания параметров командной строки, не представленных каким-либо другим параметром задачи **MT**.<br /><br /> Дополнительные сведения см. в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**AssemblyIdentity**|Необязательный параметр типа **String**.<br /><br /> Задает значения атрибута элемента **assemblyIdentity** манифеста. Укажите разделенный запятыми список, где первый компонент — это значение атрибута `name`, за которым следуют одна или несколько пар "имя-значение" в формате *\<имя_атрибута>=<значение_атрибута>*.<br /><br /> Дополнительные сведения см. в описании параметра **/identity** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ComponentFileName**|Необязательный параметр типа **String**.<br /><br /> Задает имя библиотеки динамической компоновки, которую вы планируете создать из *.rgs* или *.tlb*-файлов. Этот параметр является обязательным, если задан параметр **RegistrarScriptFile** или **TypeLibraryFile** для задачи MT.<br /><br /> Дополнительные сведения см. в описании параметра **/dll** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**DependencyInformationFile**|Необязательный параметр типа **String**.<br /><br /> Определяет файл сведений о зависимостях, используемый в Visual Studio для отслеживания зависимостей при сборке и нужный для работы инструмента манифеста.|  
|**EmbedManifest**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, файл манифеста внедряется в сборку. Если `false`, создается автономный файл манифеста.|  
|**EnableDPIAwareness**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, добавляются сведения манифеста, которые помечают приложение как поддерживающее определение DPI. При написании приложения, поддерживающего определение DPI, пользовательский интерфейс выглядит единообразно при использовании различных параметров отображения в высоком разрешении DPI.<br /><br /> Дополнительные сведения см. в разделе [Высокое DPI](https://docs.microsoft.com/windows/desktop/win7devguide/high-dpi).|  
|**GenerateCatalogFiles**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, создаются файлы определения каталога (*.cdf*).<br /><br /> Дополнительные сведения см. в описании параметра **/makecdfs** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**GenerateCategoryTags**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, создаются теги категорий. Если значение параметра равно `true`, также необходимо указать параметр задачи **ManifestFromManagedAssemblyMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/category** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**InputResourceManifests**|Необязательный параметр типа **String**.<br /><br /> Введите манифест из ресурса типа RT_MANIFEST, имеющий указанный идентификатор. Укажите ресурс в формате \<file>[;[#]\<resource_id>], где дополнительный параметр \<resource_id> — это неотрицательное 16-разрядное число.<br /><br /> Если идентификатор `resource_id` не указан, используется значение по умолчанию CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Дополнительные сведения см. в описании параметра **/inputresource** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestFromManagedAssembly**|Необязательный параметр типа **String**.<br /><br /> Создает манифест из указанной управляемой сборки.<br /><br /> Дополнительные сведения см. в описании параметра **/managedassemblyname** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestToIgnore**|Необязательный параметр типа **String**.<br /><br /> (Не используется.)|  
|**OutputManifestFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя выходного манифеста. Если этот параметр опущен и операции совершаются только с одним манифестом, то этот манифест изменяется на месте.<br /><br /> Дополнительные сведения см. в описании параметра **/out** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**OutputResourceManifests**|Необязательный параметр типа **String**.<br /><br /> Манифест выводится в ресурс типа RT_MANIFEST, имеющий указанный идентификатор. Ресурс указывается в формате \<file>[;[#]\<resource_id>], где дополнительный параметр \<resource_id> — это неотрицательное 16-разрядное число.<br /><br /> Если идентификатор `resource_id` не указан, используется значение по умолчанию CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Дополнительные сведения см. в описании параметра **/outputresource** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**RegistrarScriptFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя файла скрипта регистратора (*.rgs*), который должен использоваться для поддержки манифеста модели COM без регистрации.<br /><br /> Дополнительные сведения см. в описании параметра **/rgs** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ReplacementsFile**|Необязательный параметр типа **String**.<br /><br /> Задает файл, содержащий значения для замещаемых строк в файле скрипта регистратора (*.rgs*).<br /><br /> Дополнительные сведения см. в описании параметра **/replacements** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ResourceOutputFileName**|Необязательный параметр типа **String**.<br /><br /> Определяет выходной файл ресурсов для внедрения манифеста в выходные данные проекта.|  
|**Sources**|Необязательный параметр `ITaskItem[]` .<br /><br /> Задает список исходных файлов манифеста, разделенных пробелами.<br /><br /> Дополнительные сведения см. в описании параметра **/manifest** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressDependencyElement**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, создается манифест без элементов зависимостей. Если значение параметра равно `true`, также укажите параметр задачи **ManifestFromManagedAssemblyMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/nodependency** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressStartupBanner**|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/nologo** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**TrackerLogDirectory**|Необязательный параметр `String` .<br /><br /> Задает промежуточный каталог, в котором хранятся журналы отслеживания для этой задачи.|  
|**TypeLibraryFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя файла библиотеки типов (*.tlb*). Если этот параметр указывается, также необходимо задать параметр задачи **ComponentFileNameMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/tlb** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**UpdateFileHashes**|Необязательный параметр `Boolean` .<br /><br /> Если значение равно `true`, вычисляется значение хэша файлов по пути, указанном в параметре задачи **UpdateFileHashesSearchPathMT**, а затем значение атрибута **hash** элемента **file** манифеста обновляется с помощью полученного значения.<br /><br /> Дополнительные сведения см. в описании параметра **/hashupdate** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe). См. также описание параметра **UpdateFileHashesSearchPath** в этой таблице.|  
|**UpdateFileHashesSearchPath**|Необязательный параметр `String` .<br /><br /> Задает путь поиска для использования при обновлении хэшей файлов. Используйте этот параметр вместе с параметром задачи **UpdateFileHashesMT**.<br /><br /> Дополнительные сведения см. в описании параметра **UpdateFileHashes** в этой таблице.|  
|**VerboseOutput**|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение `true`, выводятся подробные сведения об отладке.<br /><br /> Дополнительные сведения см. в описании параметра **/verbose** в разделе [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)