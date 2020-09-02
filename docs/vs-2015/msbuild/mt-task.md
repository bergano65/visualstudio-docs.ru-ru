---
title: Задача MT | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d705bff368e813bdd2c7fe2b60ba9ada8f679bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845970"
---
# <a name="mt-task"></a>Задача MT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Является оболочкой для инструмента манифеста Майкрософт (mt.exe). Дополнительные сведения см. в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).  
  
## <a name="parameters"></a>Параметры  
 В представленной ниже таблице приводятся параметры задачи **MT**. Большинство параметров задачи и некоторые наборы параметров соответствуют параметрам командной строки.  
  
> [!NOTE]
> В документации mt.exe используется дефис ( **-** ) в качестве префикса для параметров командной строки, но в этом разделе используется косая черта ( **/** ). Допустим любой префикс.  
  
|Параметр|Description|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Необязательный параметр типа **String[]** .<br /><br /> Задает имя одного или нескольких файлов манифеста.<br /><br /> Дополнительные сведения см. в описании параметра **/manifest** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**AdditionalOptions**|Необязательный параметр **String** .<br /><br /> Список параметров командной строки. Например, "*/параметр1/параметр2/параметр№*". Этот параметр используется для указания параметров командной строки, не представленных каким-либо другим параметром задачи **MT**.<br /><br /> Дополнительные сведения см. в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**AssemblyIdentity**|Необязательный параметр **String** .<br /><br /> Задает значения атрибута элемента **assemblyIdentity** манифеста. Укажите список с разделителями-запятыми, где первым компонентом является значение `name` атрибута, за которым следуют одна или несколько пар "имя-значение", которые имеют форму, * \<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Дополнительные сведения см. в описании параметра **/identity** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**ComponentFileName**|Необязательный параметр **String** .<br /><br /> Указывает имя библиотеки динамической компоновки, сборку которой планируется выполнить из файла RGS или TLB. Этот параметр является обязательным, если задан параметр **RegistrarScriptFile** или **TypeLibraryFile** для задачи MT.<br /><br /> Дополнительные сведения см. в описании параметра **/dll** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**DependencyInformationFile**|Необязательный параметр **String** .<br /><br /> Определяет файл сведений о зависимостях, используемый в Visual Studio для отслеживания зависимостей при сборке и нужный для работы инструмента манифеста.|  
|**EmbedManifest**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, файл манифеста внедряется в сборку. Если `false`, создается автономный файл манифеста.|  
|**EnableDPIAwareness**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, добавляются сведения манифеста, которые помечают приложение как поддерживающее определение DPI. При написании приложения, поддерживающего определение DPI, пользовательский интерфейс выглядит единообразно при использовании различных параметров отображения в высоком разрешении DPI.<br /><br /> Дополнительные сведения см. в разделе "Высокий DPI" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**GenerateCatalogFiles**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, создаются файлы определения каталога (CDF-файлы).<br /><br /> Дополнительные сведения см. в описании параметра **/makecdfs** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**GenerateCategoryTags**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, создаются теги категорий. Если значение параметра равно `true`, также необходимо указать параметр задачи **ManifestFromManagedAssemblyMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/category** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**InputResourceManifests**|Необязательный параметр **String** .<br /><br /> Введите манифест из ресурса типа RT_MANIFEST, имеющий указанный идентификатор. Укажите ресурс в форме, _ \<file> [_**;** _[_ **#** _] <resource_id>]_, где необязательный `resource_id` параметр имеет неотрицательное 16-разрядное число.<br /><br /> Если идентификатор `resource_id` не указан, используется значение по умолчанию CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Дополнительные сведения см. в описании параметра **/inputresource** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**ManifestFromManagedAssembly**|Необязательный параметр **String** .<br /><br /> Создает манифест из указанной управляемой сборки.<br /><br /> Дополнительные сведения см. в описании параметра **/managedassemblyname** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**ManifestToIgnore**|Необязательный параметр **String** .<br /><br /> (Не используется.)|  
|**OutputManifestFile**|Необязательный параметр **String** .<br /><br /> Задает имя выходного манифеста. Если этот параметр опущен и операции совершаются только с одним манифестом, то этот манифест изменяется на месте.<br /><br /> Дополнительные сведения см. в описании параметра **/out** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**OutputResourceManifests**|Необязательный параметр **String** .<br /><br /> Манифест выводится в ресурс типа RT_MANIFEST, имеющий указанный идентификатор. Ресурс имеет форму _ \<file> [_**;** _[_ **#** _] <resource_id>]_, где необязательный `resource_id` параметр имеет неотрицательное 16-разрядное число.<br /><br /> Если идентификатор `resource_id` не указан, используется значение по умолчанию CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Дополнительные сведения см. в описании параметра **/outputresource** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**RegistrarScriptFile**|Необязательный параметр **String** .<br /><br /> Задает имя файла скрипта регистратора (RGS-файла), который должен использоваться для поддержки манифеста модели COM без регистрации.<br /><br /> Дополнительные сведения см. в описании параметра **/rgs** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**ReplacementsFile**|Необязательный параметр **String** .<br /><br /> Указывает файл, содержащий значения для замещаемых строк в файле скрипта регистратора (RGS-файле).<br /><br /> Дополнительные сведения см. в описании параметра **/replacements** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**ResourceOutputFileName**|Необязательный параметр **String** .<br /><br /> Определяет выходной файл ресурсов для внедрения манифеста в выходные данные проекта.|  
|**Источники**|Необязательный параметр `ITaskItem[]`.<br /><br /> Задает список исходных файлов манифеста, разделенных пробелами.<br /><br /> Дополнительные сведения см. в описании параметра **/manifest** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**SuppressDependencyElement**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, создается манифест без элементов зависимостей. Если значение параметра равно `true`, также укажите параметр задачи **ManifestFromManagedAssemblyMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/nodependency** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**SuppressStartupBanner**|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/nologo** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**TrackerLogDirectory**|Необязательный параметр `String`.<br /><br /> Задает промежуточный каталог, в котором хранятся журналы отслеживания для этой задачи.|  
|**TypeLibraryFile**|Необязательный параметр **String** .<br /><br /> Задает имя файла библиотеки типов (TLB-файла). Если этот параметр указывается, также необходимо задать параметр задачи **ComponentFileNameMT**.<br /><br /> Дополнительные сведения см. в описании параметра **/tlb** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
|**UpdateFileHashes**|Необязательный параметр `Boolean`.<br /><br /> Если значение равно `true`, вычисляется значение хэша файлов по пути, указанном в параметре задачи **UpdateFileHashesSearchPathMT**, а затем значение атрибута **hash** элемента **file** манифеста обновляется с помощью полученного значения.<br /><br /> Дополнительные сведения см. в описании параметра **/hashupdate** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/). См. также описание параметра **UpdateFileHashesSearchPath** в этой таблице.|  
|**UpdateFileHashesSearchPath**|Необязательный параметр `String`.<br /><br /> Задает путь поиска для использования при обновлении хэшей файлов. Используйте этот параметр вместе с параметром задачи **UpdateFileHashesMT**.<br /><br /> Дополнительные сведения см. в описании параметра **UpdateFileHashes** в этой таблице.|  
|**VerboseOutput**|Необязательный параметр `Boolean`.<br /><br /> Если имеет значение `true`, выводятся подробные сведения об отладке.<br /><br /> Дополнительные сведения см. в описании параметра **/verbose** в разделе "Mt.exe" на веб-сайте [MSDN](https://msdn.microsoft.com/).|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
