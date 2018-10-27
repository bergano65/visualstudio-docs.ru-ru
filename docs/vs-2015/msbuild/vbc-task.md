---
title: Задача Vbc| Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f97e3ad4321cb8503a964115922f06e62f2c121
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143428"
---
# <a name="vbc-task"></a>Задача Vbc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Использует программу-оболочку для файла vbc.exe, который создает исполняемые файлы (EXE-файлы), библиотеки динамической компоновки (DLL-файлы) или модули кода (.netmodule). Дополнительные сведения о файле vbc.exe. см. в разделе [Компилятор Visual Basic с интерфейсом командной строки](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `Vbc` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Необязательный параметр `String[]` .<br /><br /> Задает дополнительные папки, в которых выполняется поиск сборок, указанных в атрибуте References.|  
|`AddModules`|Необязательный параметр `String[]` .<br /><br /> Дает компилятору указание сделать всю информацию о типах из указанных файлов доступной компилируемому проекту. Этот параметр соответствует параметру [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) компилятора vbc.exe.|  
|`BaseAddress`|Необязательный параметр `String` .<br /><br /> Задает базовый адрес библиотеки DLL. Этот параметр соответствует параметру [/baseaddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) компилятора vbc.exe.|  
|`CodePage`|Необязательный параметр `Int32` .<br /><br /> Задает кодовую страницу, которая будет использоваться для всех файлов исходного кода при компиляции. Этот параметр соответствует параметру [/codepage](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) компилятора vbc.exe.|  
|`DebugType`|Необязательный параметр `String[]` .<br /><br /> Указывает компилятору создать отладочную информацию. Этот параметр может иметь следующие значения:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> По умолчанию задано значение `full`, разрешающее подключение отладчика к исполняемой программе. Значение `pdbonly` позволяет выполнять отладку исходного кода при запуске программы в отладчике, но при этом код языка сборки отображается только при подключении выполняющейся программы к отладчику. Дополнительные сведения см. в разделе [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Необязательный параметр `String[]` .<br /><br /> Задает константы условной компиляции. Пары "символ — значение" разделяются точками с запятой и задаются с использованием следующего синтаксиса.<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Этот параметр соответствует параметру [/define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) компилятора vbc.exe.|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, задача помещает открытый ключ в сборку. Если присвоено значение `false`, задача полностью подписывает сборку. Значение по умолчанию — `false`. Этот параметр действует только при использовании параметра `KeyFile` или `KeyContainer`. Этот параметр соответствует параметру [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) компилятора vbc.exe.|  
|`DisabledWarnings`|Необязательный параметр `String` .<br /><br /> Подавляет указанные предупреждения. Необходимо указать только числовую часть идентификатора предупреждения. При указании нескольких предупреждений они отделяются друг от друга точкой с запятой. Этот параметр соответствует параметру [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) компилятора vbc.exe.|  
|`DocumentationFile`|Необязательный параметр `String` .<br /><br /> Обрабатывает комментарии к документации в указанный XML-файл. Этот параметр переопределяет атрибут `GenerateDocumentation`. Дополнительные сведения см. в разделе [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, задача генерирует отладочную информацию и помещает ее в PDB-файл. Дополнительные сведения см. в разделе [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Необязательный параметр `String` .<br /><br /> Указывает, как задача должна сообщать о внутренних ошибках компилятора. Этот параметр может иметь следующие значения:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Если присвоено значение `prompt`, при возникновении внутренней ошибки компилятора пользователю предлагается возможность отправить сведения ошибке в корпорацию Майкрософт.<br /><br /> Если присвоено значение, `send` при возникновении внутренней ошибки компилятора задача отправляет данные об ошибке в корпорацию Майкрософт.<br /><br /> Значение по умолчанию — `none`, при котором сообщение об ошибке отправляется только в виде текста.<br /><br /> Этот параметр соответствует параметру [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) компилятора vbc.exe.|  
|`FileAlignment`|Необязательный параметр `Int32` .<br /><br /> Задает выравнивание размеров выходного файла в байтах. Этот параметр может иметь следующие значения:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Этот параметр соответствует параметру [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) компилятора vbc.exe.|  
|`GenerateDocumentation`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, в процессе сборки создается информация документации и помещается в XML-файл вместе с именем исполняемого файла или библиотеки, созданных задачей. Дополнительные сведения см. в разделе [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Импорт пространства имен из указанных коллекций элементов. Этот параметр соответствует параметру [/imports](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) компилятора vbc.exe.|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает имя контейнера криптографического ключа. Этот параметр соответствует параметру [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) компилятора vbc.exe.|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Задает имя файла, содержащего криптографический ключ. Дополнительные сведения см. в разделе [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Необязательный [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) параметра.<br /><br /> Задает используемую версию языка ("9" или "10").|  
|`LinkResources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Создается ссылка на ресурс .NET Framework в выходном файле. Файл ресурса не помещается в выходной файл. Этот параметр соответствует параметру [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) компилятора vbc.exe.|  
|`MainEntryPoint`|Необязательный параметр `String` .<br /><br /> Задает класс или модуль, содержащий процедуру `Sub Main`. Этот параметр соответствует параметру [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) компилятора vbc.exe.|  
|`ModuleAssemblyName`|Необязательный параметр `String` .<br /><br /> Задает сборку, частью которой будет этот модуль.|  
|`NoConfig`|Необязательный параметр `Boolean` .<br /><br /> Указывает, что компилятору не следует использовать файл vbc.rsp. Этот параметр соответствует параметру [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) компилятора vbc.exe.|  
|`NoLogo`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, отображение заголовка компилятора отключается. Этот параметр соответствует параметру [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) компилятора vbc.exe.|  
|`NoStandardLib`|Необязательный параметр `Boolean` .<br /><br /> Указывает компилятору не ссылаться на стандартные библиотеки. Этот параметр соответствует параметру [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) компилятора vbc.exe.|  
|`NoVBRuntimeReference`|Необязательный параметр `Boolean` .<br /><br /> Только для внутреннего использования. Если присвоено значение true, предотвращает автоматическую ссылку на Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, задача отключает все предупреждения. Дополнительные сведения см. в статье [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение`true`, разрешает оптимизацию компилятора. Этот параметр соответствует параметру [/optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) компилятора vbc.exe.|  
|`OptionCompare`|Необязательный параметр `String` .<br /><br /> Задает способ сравнения строк. Этот параметр может иметь следующие значения:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Значение `binary` указывает на то, что в задаче используются двоичные сравнения строк. Значение `text` указывает на то, что в задаче используются текстовые сравнения строк. По умолчанию этот параметр имеет значение `binary`. Этот параметр соответствует параметру [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) компилятора vbc.exe.|  
|`OptionExplicit`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, требуется явное объявление переменных. Этот параметр соответствует параметру [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) компилятора vbc.exe.|  
|`OptionInfer`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, для переменных разрешено определение типа.|  
|`OptionStrict`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, задача применяет строгую семантику типа и ограничивает неявное преобразование типов. Этот параметр соответствует параметру [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) компилятора vbc.exe.|  
|`OptionStrictType`|Необязательный параметр `String` .<br /><br /> Указывает, какая строгая семантика типа генерирует предупреждение. В настоящее время поддерживается только custom. Этот параметр соответствует параметру [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) компилятора vbc.exe.|  
|`OutputAssembly`|Необязательный выходной параметр `String`.<br /><br /> Задает имя выходного файла. Этот параметр соответствует параметру [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) компилятора vbc.exe.|  
|`Platform`|Необязательный параметр `String` .<br /><br /> Указывает целевую платформу процессора для выходного файла. Этот параметр может иметь значение `x86`, `x64`, `Itanium` или `anycpu`. Значение по умолчанию — `anycpu`. Этот параметр соответствует параметру [/platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) компилятора vbc.exe.|  
|`References`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Вызывает импорт задачей информации об открытых типах из заданных элементов в текущий проект. Этот параметр соответствует параметру [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) компилятора vbc.exe.|  
|`RemoveIntegerChecks`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, отключает проверку переполнения для целочисленных значений. Значение по умолчанию — `false`. Этот параметр соответствует параметру [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) компилятора vbc.exe.|  
|`Resources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Внедряет ресурс .NET Framework в выходной файл. Этот параметр соответствует параметру [/resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) компилятора vbc.exe.|  
|`ResponseFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает файл ответов, содержащий команды для этой задачи. Этот параметр соответствует параметру [@ (указание файла ответа)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) компилятора vbc.exe.|  
|`RootNamespace`|Необязательный параметр `String` .<br /><br /> Задает корневое пространство имен для всех объявлений типов. Этот параметр соответствует параметру [/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) компилятора vbc.exe.|  
|`SdkPath`|Необязательный параметр `String` .<br /><br /> Задает расположение библиотек mscorlib.dll и microsoft.visualbasic.dll. Этот параметр соответствует параметру [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) компилятора vbc.exe.|  
|`Sources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает один или несколько файлов исходного кода [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`TargetCompactFramework`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, задача выбирает [!INCLUDE[Compact](../includes/compact-md.md)] в качестве целевого объекта. Этот параметр соответствует параметру [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) компилятора vbc.exe.|  
|`TargetType`|Необязательный параметр `String` .<br /><br /> Задает формат выходного файла. Этот параметр может принимать одно из следующих значений: `library` (создается библиотека кода), `exe` (создается консольное приложение), `module` (создается модуль) или `winexe` (создается программа Windows). Значение по умолчанию — `library`. Этот параметр соответствует параметру [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) компилятора vbc.exe.|  
|`Timeout`|Необязательный параметр `Int32` .<br /><br /> Задает промежуток времени в миллисекундах, после которого исполняемый файл задачи прекращается. Значение по умолчанию — `Int.MaxValue`. Оно указывает, что период ожидания отсутствует.|  
|`ToolPath`|Необязательный параметр `String` .<br /><br /> Указывает расположение, из которого задача будет загружать базовый исполняемый файл (vbc.exe). Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии платформы, на которой выполняется [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, все предупреждения обрабатываются как ошибки. Дополнительные сведения см. в разделе [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Необязательный параметр `Boolean` .<br /><br /> Предписывает задаче использовать внутрипроцессный объект компилятора, если он доступен. Используется только в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Необязательный параметр `Boolean` .<br /><br /> Регистрирует выходные данные компилятора в кодировке UTF-8. Этот параметр соответствует параметру [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) компилятора vbc.exe.|  
|`Verbosity`|Необязательный параметр `String` .<br /><br /> Задает уровень детализации выходных данных компилятора. Уровень детализации может быть `Quiet`, `Normal` (по умолчанию) или `Verbose`.|  
|`WarningsAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Этот параметр переопределяет параметр `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Этот параметр имеет смысл только в том случае, если для параметра `TreatWarningsAsErrors` задано значение `true`.|  
|`Win32Icon`|Необязательный параметр `String` .<br /><br /> Вставляет ICO-файл в сборку, которая придает выходному файлу необходимый вид в проводнике. Этот параметр соответствует параметру [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) компилятора vbc.exe.|  
|`Win32Resources`|Необязательный параметр `String` .<br /><br /> Вставляет файл ресурсов Win32 (RES-файл) в выходной файл. Этот параметр соответствует параметру [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) компилятора vbc.exe.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере компилируется проект [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



