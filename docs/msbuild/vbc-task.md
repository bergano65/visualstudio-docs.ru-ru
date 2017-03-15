---
title: "Задача Vbc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Vbc - задача"
  - "Vbc - задача [MSBuild]"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Задача Vbc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает программу\-оболочку для компилятора vbc.exe, создающего исполняемые файлы \(EXE\-файлы\), библиотеки динамической компоновки \(DLL\-файлы\) и модули кода \(  NETMODULE\).  Дополнительные сведения о программе vbc.exe см. в разделе [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Параметры  
 В следующей таблице описаны параметры задачи `Vbc`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AdditionalLibPaths`|Необязательный параметр типа `String[]`.<br /><br /> Задает дополнительные папки, в которых производится поиск сборок, указанных в атрибуте References.|  
|`AddModules`|Необязательный параметр типа `String[]`.<br /><br /> Делает доступными все сведения из указанных файлов для компилируемого проекта.  Этот параметр соответствует ключу [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) компилятора vbc.exe.|  
|`BaseAddress`|Необязательный параметр типа `String`.<br /><br /> Задает базовый адрес библиотеки DLL.  Этот параметр соответствует ключу [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) компилятора vbc.exe.|  
|`CodePage`|Необязательный параметр типа `Int32`.<br /><br /> Задает кодовую страницу, используемую для всех файлов исходного кода при компиляции.  Этот параметр соответствует ключу [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) компилятора vbc.exe.|  
|`DebugType`|Необязательный параметр типа `String[]`.<br /><br /> Указывает компилятору создавать отладочную информацию.  Этот параметр может принимать следующие значения:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> По умолчанию используется значение `full`, которое позволяет присоединить отладчик к выполняющейся программе.  Значение `pdbonly` позволяет выполнить отладку исходного кода при запуске программы в отладчике, но ассемблерный код отображается только тогда, когда запущенная программа присоединяется к отладчику.  Дополнительные сведения см. в разделе [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Необязательный параметр типа `String[]`.<br /><br /> Определение констант условной компиляции.  Пары символ\/значение разделяются точками с запятой и задаются с помощью следующего синтаксиса:<br /><br /> *символ\_1* `=` *значение\_1* `;` *символ\_2* `=` *значение\_2*<br /><br /> Этот параметр соответствует ключу [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) компилятора vbc.exe.|  
|`DelaySign`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, задача добавляет в сборку открытый ключ.  Если этот параметре имеет значение `false`, задача полностью подписывает сборку.  По умолчанию используется значение `false`. Этот параметр не оказывает никакого влияния, если он не используется вместе с параметром `KeyFile` или с параметром `KeyContainer`.  Этот параметр соответствует ключу [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) компилятора vbc.exe.|  
|`DisabledWarnings`|Необязательный параметр типа `String`.<br /><br /> Отключает указанные предупреждения.  Необходимо указать только числовую часть идентификатора предупреждения.  Несколько предупреждений отделяются друг от друга точкой с запятой.  Этот параметр соответствует ключу [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) компилятора vbc.exe.|  
|`DocumentationFile`|Необязательный параметр типа `String`.<br /><br /> Помещает комментарии для документации в указанный XML\-файл.  Этот параметр переопределяет атрибут `GenerateDocumentation`.  Дополнительные сведения см. в разделах [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, задача создает отладочную информацию и помещает ее в PDB\-файл.  Дополнительные сведения см. в разделе [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Необязательный параметр типа `String`.<br /><br /> Указывает, как задача должна сообщать о внутренних ошибках компилятора.  Этот параметр может принимать следующие значения:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Если используется значение `prompt`, при возникновении внутренних ошибок компилятора пользователь получает сообщение с предложением отправить данные об ошибке в корпорацию Майкрософт.<br /><br /> Если используется значение `send`, при возникновении внутренних ошибок компилятора задача самостоятельно отправляет данные об ошибке в корпорацию Майкрософт.<br /><br /> По умолчанию используется значение `none`, при котором выводится только текст сообщения об ошибке.<br /><br /> Этот параметр соответствует ключу [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) компилятора vbc.exe.|  
|`FileAlignment`|Необязательный параметр типа `Int32`.<br /><br /> Определение \(в байтах\), где выровнять разделы выходного файла.  Этот параметр может принимать следующие значения:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Этот параметр соответствует ключу [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) компилятора vbc.exe.|  
|`GenerateDocumentation`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, генерируются комментарии для документации и помещаются в XML\-файл вместе с именем выполняемого файла или библиотеки, которые созданы задачей.  Дополнительные сведения см. в разделах [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Осуществляет импорт пространства имен из указанных коллекций элементов.  Этот параметр соответствует ключу [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) компилятора vbc.exe.|  
|`KeyContainer`|Необязательный параметр типа `String`.<br /><br /> Задает имя контейнера криптографического ключа.  Этот параметр соответствует ключу [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) компилятора vbc.exe.|  
|`KeyFile`|Необязательный параметр типа `String`.<br /><br /> Задает имя файла, содержащего криптографический ключ.  Дополнительные сведения см. в разделе [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Необязательный параметр типа [String](assetId:///String?qualifyHint=False&autoUpgrade=True).<br /><br /> Указывает версию языка, «9»или «10».|  
|`LinkResources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Создает ссылку на ресурс .NET Framework в выходном файле; не включает файл ресурса в выходной файл.  Этот параметр соответствует ключу [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) компилятора vbc.exe.|  
|`MainEntryPoint`|Необязательный параметр типа `String`.<br /><br /> Указывает класс или модуль, содержащий процедуру `Sub Main`.  Этот параметр соответствует ключу [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) компилятора vbc.exe.|  
|`ModuleAssemblyName`|Необязательный параметр типа `String`.<br /><br /> Указывает сборку, частью которой является этот модуль.|  
|`NoConfig`|Необязательный параметр типа `Boolean`.<br /><br /> Предписывает компилятору не использовать файл vbc.rsp.  Этот параметр соответствует параметру [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) компилятора vbc.exe.|  
|`NoLogo`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, отображение заголовка компилятора отключается.  Этот параметр соответствует ключу [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) компилятора vbc.exe.|  
|`NoStandardLib`|Необязательный параметр типа `Boolean`.<br /><br /> Предписывает компилятору не ссылаться на стандартные библиотеки.  Этот параметр соответствует ключу [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) компилятора vbc.exe.|  
|`NoVBRuntimeReference`|Необязательный параметр типа `Boolean`.<br /><br /> Только для внутреннего использования.  Если true, предотвращает автоматическое ссылки на библиотеку Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, все предупреждения будут отключены.  Дополнительные сведения см. в разделе [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Необязательный параметр типа `Boolean`.<br /><br /> Значение `true` включает оптимизацию компилятора.  Этот параметр соответствует ключу [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) компилятора vbc.exe.|  
|`OptionCompare`|Необязательный параметр типа `String`.<br /><br /> Задает способ сравнения строк.  Этот параметр может принимать следующие значения:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Значение `binary` указывает задаче использовать двоичное сравнение строк.  Значение `text` указывает задаче использовать текстовое сравнение строк.  По умолчанию этот параметр имеет значение `binary`.  Этот параметр соответствует ключу [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) компилятора vbc.exe.|  
|`OptionExplicit`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, необходимо  явное объявление переменных.  Этот параметр соответствует ключу [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) компилятора vbc.exe.|  
|`OptionInfer`|Необязательный параметр типа `Boolean`.<br /><br /> `true` разрешает вывод типа переменных.|  
|`OptionStrict`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, задача применяет семантику строгого типа для ограничения неявных преобразований типов.  Этот параметр соответствует ключу [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) компилятора vbc.exe.|  
|`OptionStrictType`|Необязательный параметр типа `String`.<br /><br /> Определяет, какая семантика строгого типа создает предупреждение.  В настоящее время только "custom" поддерживается.  Этот параметр соответствует ключу [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) компилятора vbc.exe.|  
|`OutputAssembly`|Необязательный выходной параметр типа `String`.<br /><br /> Задает имя выходного файла.  Этот параметр соответствует ключу [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) компилятора vbc.exe.|  
|`Platform`|Необязательный параметр типа `String`.<br /><br /> Задает платформу процессора, для которой следует создавать выходной файл.  Этот параметр может иметь следующие значения: `x86`, `x64`, `Itanium` или `anycpu`.  По умолчанию используется значение `anycpu`.  Этот параметр соответствует ключу [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) компилятора vbc.exe.|  
|`References`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Вызывает импорт задачей информации об открытых типах из заданных элементов в текущий проект.  Этот параметр соответствует ключу [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) компилятора vbc.exe.|  
|`RemoveIntegerChecks`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, проверки целочисленного переполнения отключены.  Значение по умолчанию — `false`.  Этот параметр соответствует ключу [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) компилятора vbc.exe.|  
|`Resources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Включает ресурс .NET Framework в выходной файл.  Этот параметр соответствует ключу [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) компилятора vbc.exe.|  
|`ResponseFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает файл ответов, содержащий команды для данной задачи.  Этот параметр соответствует параметру [@ \(Specify Response File\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) компилятора vbc.exe.|  
|`RootNamespace`|Необязательный параметр типа `String`.<br /><br /> Указывает корневое пространство имен для всех объявлений типов.  Этот параметр соответствует ключу [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) компилятора vbc.exe.|  
|`SdkPath`|Необязательный параметр типа `String`.<br /><br /> Указывает расположение библиотек mscorlib.dll и microsoft.visualbasic.dll.  Этот параметр соответствует ключу [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) компилятора vbc.exe.|  
|`Sources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает один или несколько исходных файлов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] является для задачи целевой платформой.  Этот параметр соответствует ключу [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) компилятора vbc.exe.|  
|`TargetType`|Необязательный параметр типа `String`.<br /><br /> Задает формат выходного файла.  Этот параметр может принимать одно из следующих значений: `library` \(создается библиотека кода\), `exe` \(создается консольное приложение\), `module` \(создается модуль\) или `winexe` \(создается Windows\-программа\).  По умолчанию используется значение `library`.  Этот параметр соответствует ключу [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) компилятора vbc.exe.|  
|`Timeout`|Необязательный параметр типа `Int32`.<br /><br /> Указывает временной интервал в миллисекундах, по истечении которого исполнение файла задачи останавливается.  Значение по умолчанию `Int.MaxValue` указывает, что таймаут не задан.|  
|`ToolPath`|Необязательный параметр типа `String`.<br /><br /> Указывает расположение, откуда задача будет загружать базовый исполняемый файл \(vbc.exe\).  Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии среды, в которой выполняется [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, все предупреждения обрабатываются как ошибки.  Дополнительные сведения см. в разделе [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Необязательный параметр типа `Boolean`.<br /><br /> Предписывает задаче использовать внутрипроцессный объект компилятора, если он доступен.  Используется только [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Необязательный параметр типа `Boolean`.<br /><br /> Регистрирует выходные данные компилятора в кодировке UTF\-8.  Этот параметр соответствует ключу [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) компилятора vbc.exe.|  
|`Verbosity`|Необязательный параметр типа `String`.<br /><br /> Задает уровень детализации выходных данных компилятора.  Детализация может иметь значение `Quiet`, `Normal` \(по умолчанию\) или `Verbose`.|  
|`WarningsAsErrors`|Необязательный параметр типа `String`.<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки.  Дополнительные сведения см. в разделе [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Этот параметр переопределяет параметр `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Необязательный параметр типа `String`.<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки.  Дополнительные сведения см. в разделе [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Этот параметр имеет смысл только в том случае, если параметр `TreatWarningsAsErrors` имеет значение `true`.|  
|`Win32Icon`|Необязательный параметр типа `String`.<br /><br /> Вставляет ico\-файл в сборку, которая присваивает выходному файлу нужного обозревателе файла внешнего вида.  Этот параметр соответствует ключу [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) компилятора vbc.exe.|  
|`Win32Resources`|Необязательный параметр типа `String`.<br /><br /> Внедряет файл ресурсов Win32 \(RES\-файл\) в выходной файл.  Этот параметр соответствует ключу [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) компилятора vbc.exe.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## Пример  
 В следующем примере демонстрируется компиляция проекта [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)