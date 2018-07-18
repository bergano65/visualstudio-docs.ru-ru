---
title: Задача LIB | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69dec38691969eafa92a13dea0333fbc17060354
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574224"
---
# <a name="lib-task"></a>Задача LIB
Заключает в оболочку 32-разрядный диспетчер библиотек Майкрософт lib.exe. Диспетчер библиотек создает библиотеку объектных файлов в формате COFF и управляет ею. Диспетчер библиотек также может создавать файлы экспорта и импортировать библиотеки в экспортированные справочные определения. Дополнительные сведения см. в разделах [Справочник по LIB](/cpp/build/reference/lib-reference) и [Запуск программы LIB](/cpp/build/reference/running-lib).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи **LIB**. Большинство параметров задач соответствуют параметрам командной строки.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|**AdditionalDependencies**|Необязательный параметр типа **String[]**.<br /><br /> Указывает дополнительные элементы для добавления в командную строку.|  
|**AdditionalLibraryDirectories**|Необязательный параметр типа **String[]**.<br /><br /> Переопределяет путь к библиотеке среды. Задает имя каталога.<br /><br /> Дополнительные сведения см. в разделе [Параметр /LIBPATH (дополнительный параметр Libpath)](/cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|Необязательный параметр типа **String**.<br /><br /> Список параметров lib.exe, как указано в командной строке. Например, **"***/параметр1 /параметр2 /параметр#*". Этот параметр используется для указания параметров lib.exe, не представленных каким-либо другим параметром задачи **LIB**.<br /><br /> Дополнительные сведения см. в разделе [Запуск программы LIB](/cpp/build/reference/running-lib).|  
|**DisplayLibrary**|Необязательный параметр типа **String**.<br /><br /> Отображает сведения о выходной библиотеке. Укажите имя файла для перенаправления сведений в файл. Укажите «CON» или ничего для перенаправления сведений на консоль.<br /><br /> Этот параметр соответствует параметру **/LIST** в lib.exe.|  
|**ErrorReporting**|Необязательный параметр типа **String**.<br /><br /> Указывает способ отправки сведений о внутренней ошибке в Майкрософт при сбое lib.exe во время выполнения.<br /><br /> Укажите одно из следующих значений, каждое из которых соответствует параметру командной строки.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Дополнительные сведения см. в описании параметра командной строки **/ERRORREPORT** в разделе [Запуск программы LIB](/cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|Необязательный параметр типа **String[]**.<br /><br /> Указывает одну или несколько функций для экспорта.<br /><br /> Этот параметр соответствует параметру **/EXPORT:** в lib.exe.|  
|**ForceSymbolReferences**|Необязательный параметр типа **String**.<br /><br /> Заставляет lib.exe включать ссылку на указанный символ.<br /><br /> Этот параметр соответствует параметру **/INCLUDE:** в lib.exe.|  
|**IgnoreAllDefaultLibraries**|Необязательный параметр `Boolean` .<br /><br /> Если указано значение `true`, то из списка библиотек, в котором lib.exe выполняет поиск при разрешении внешних ссылок, будут удалены все стандартные библиотеки.<br /><br /> Этот параметр соответствует форме параметра **/NODEFAULTLIB** без параметров в lib.exe.|  
|**IgnoreSpecificDefaultLibraries**|Необязательный параметр типа **String[]**.<br /><br /> Удаляет указанные библиотеки из списка библиотек, в котором lib.exe выполняет поиск при разрешении внешних ссылок.<br /><br /> Этот параметр соответствует параметру **/NODEFAULTLIB** в lib.exe, который принимает аргумент `library`.|  
|**LinkLibraryDependencies**|Необязательный параметр `Boolean` .<br /><br /> Значение `true` указывает, что выходные данные библиотеки из зависимостей проекта включаются автоматически.|  
|**LinkTimeCodeGeneration**|Необязательный параметр `Boolean` .<br /><br /> Значение `true` задает создание кода во время компоновки.<br /><br /> Этот параметр соответствует параметру **/LCTG** в lib.exe.|  
|**MinimumRequiredVersion**|Необязательный параметр типа **String**.<br /><br /> Задает минимальную необходимую версию подсистемы. Укажите разделенный запятыми список десятичных чисел в диапазоне от 0 до 65535.|  
|**ModuleDefinitionFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя файла определения модуля (DEF-файла).<br /><br /> Этот параметр соответствует параметру **/DEF** в lib.exe, который принимает аргумент `filename`.|  
|**Name**|Необязательный параметр типа **String**.<br /><br /> При сборке библиотеки импорта задает имя DLL, для которой собирается библиотека импорта.<br /><br /> Этот параметр соответствует параметру **/NAME** в lib.exe, который принимает аргумент `filename`.|  
|**OutputFile**|Необязательный параметр типа **String**.<br /><br /> Переопределяет заданное по умолчанию имя и расположение программы, создаваемой lib.exe.<br /><br /> Этот параметр соответствует параметру **/OUT** в lib.exe, который принимает аргумент `filename`.|  
|**RemoveObjects**|Необязательный параметр типа **String[]**.<br /><br /> Исключает указанный объект из выходной библиотеки. Lib.exe создает выходную библиотеку, объединяя все объекты (в объектных файлах или в библиотеках), а затем удаляет все объекты, указанные этим параметром.<br /><br /> Этот параметр соответствует параметру **/REMOVE** в lib.exe, который принимает аргумент `membername`.|  
|**Sources**|Обязательный параметр `ITaskItem[]` .<br /><br /> Задает список исходных файлов, разделенных пробелами.|  
|**SubSystem**|Необязательный параметр типа **String**.<br /><br /> Указывает среду для исполняемого файла. Выбор подсистемы влияет на символ точки входа или функцию точки входа.<br /><br /> Укажите одно из следующих значений, каждое из которых соответствует параметру командной строки.<br /><br /> -   **Console** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Native** - **/SUBSYSTEM:NATIVE**<br />-   **Приложение EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI-драйвер службы загрузки** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI-среда выполнения** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**ReplaceThisText<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Дополнительные сведения см. в разделе [Параметр /SUBSYSTEM (определение подсистемы)](/cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/NOLOGO** в разделе [Запуск программы LIB](/cpp/build/reference/running-lib).|  
|**TargetMachine**|Необязательный параметр типа **String**.<br /><br /> Задает целевую платформу программы или DLL.<br /><br /> Укажите одно из следующих значений, каждое из которых соответствует параметру командной строки.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Дополнительные сведения см. в разделе [Параметр /MACHINE (определение целевой платформы)](/cpp/build/reference/machine-specify-target-platform).|  
|**TrackerLogDirectory**|Необязательный параметр типа **String**.<br /><br /> Задает каталог журнала отслеживания.|  
|**TreatLibWarningAsErrors**|Необязательный параметр типа **Boolean**.<br /><br /> Значение `true` приводит к тому, что задача **LIB** не создает выходной файл, если lib.exe создает предупреждение. Если указано значение `false`, выходной файл создается.<br /><br /> Дополнительные сведения см. в описании параметра **/WX** в разделе [Запуск программы LIB](/cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|Необязательный параметр типа **Boolean**.<br /><br /> Значение `true` предписывает системе проектов создавать файлы ответа в Юникоде, когда порождается библиотекарь. Укажите значение `true`, если файлы в проекте имеют пути в Юникоде.|  
|**Verbose**|Необязательный параметр типа **Boolean**.<br /><br /> Если указано значение `true`, то отображаются сведения о ходе выполнения сеанса, включая имена добавляемых OBJ-файлов. Эти сведения отправляются в стандартный вывод и могут быть перенаправлены в файл.<br /><br /> Дополнительные сведения см. в описании параметра **/VERBOSE** в разделе [Запуск программы LIB](/cpp/build/reference/running-lib).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)