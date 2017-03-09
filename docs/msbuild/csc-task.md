---
title: "Задача Csc | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc - задача [MSBuild]"
  - "MSBuild Csc-задача"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача Csc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Выполняет программу CSC.exe и создает исполняемые (файлы.exe), библиотеки динамической компоновки (DLL-файлы) и модули кода (NETMODULE-файлы). Дополнительные сведения о CSC.exe см. в разделе [Параметры компилятора C#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `Csc`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Необязательный параметр `String[]` .<br /><br /> Задает дополнительные каталоги для поиска ссылок. Дополнительные сведения см. в разделе [/lib (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Необязательный параметр `String` .<br /><br /> Задает один или несколько модулей, которые должны быть частью сборки. Дополнительные сведения см. в разделе [/addmodule (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, компилирует код, использующий [небезопасные](/dotnet/csharp/language-reference/keywords/unsafe) ключевое слово. Дополнительные сведения см. в разделе [/ unsafe (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Необязательный параметр `String` .<br /><br /> Задает файл конфигурации приложения, содержащий параметры привязки сборки.|  
|`BaseAddress`|Необязательный параметр `String` .<br /><br /> Указывает предпочтительный базовый адрес для загрузки DLL. Базовый адрес библиотеки DLL по умолчанию задается [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] среды CLR. Дополнительные сведения см. в разделе [/baseaddress (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Необязательный параметр `Boolean` .<br /><br /> Указывает, должны ли целочисленные арифметические операции, вызывающие переполнение типа данных, вызывать исключение во время выполнения. Дополнительные сведения см. в разделе [/ checked (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Необязательный параметр `Int32`.<br /><br /> Задает кодовую страницу, которая будет использоваться для всех файлов исходного кода при компиляции. Дополнительные сведения см. в разделе [/codepage (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Необязательный параметр `String` .<br /><br /> Задает тип отладки. `DebugType` может быть `full` или `pdbonly`. Значение по умолчанию — `full`, который позволяет отладчику должны быть присоединены к выполняющейся программе. Указание `pdbonly` источника позволяет отлаживать код, когда программа запускается в отладчике, но ассемблерный код отображается только когда запущенная программа присоединяется к отладчику.<br /><br /> Этот параметр переопределяет `EmitDebugInformation` параметр.<br /><br /> Дополнительные сведения см. в разделе [/Debug (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Необязательный параметр `String` .<br /><br /> Определяет символы препроцессора. Дополнительные сведения см. в разделе [/ define (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, указывает, что требуется полностью подписанная сборка. Если `false`, указывает, что необходимо только поместить открытый ключ в сборку.<br /><br /> Этот параметр действует только при использовании либо `KeyFile` или `KeyContainer` параметра.<br /><br /> Дополнительные сведения см. в разделе [/delaysign (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые требуется отключить. Дополнительные сведения см. в разделе [/nowarn (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Необязательный параметр `String` .<br /><br /> Обрабатывает комментарии к документации в XML-файл. Дополнительные сведения см. в разделе [/doc (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, задача создает отладочную информацию и помещает ее в PDB-файл программы. Если `false`, задача не генерирует отладочную информацию. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [/Debug (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Необязательный параметр `String` .<br /><br /> Предоставляет удобный способ сообщить Внутренняя ошибка в C# в корпорацию Майкрософт. Этот параметр может иметь значение `prompt`, `send`, или `none`. Если параметр имеет значение `prompt`, получат запрос при возникновении внутренней ошибки компилятора. Запрос позволяет электронным образом отправлять отчет об ошибках в корпорацию Майкрософт. Если параметр имеет значение `send`, сообщение об ошибке отправляется автоматически. Если параметр имеет значение `none`, отчет об ошибке выводится только в текстовых выходных данных компилятора. Значение по умолчанию — `none`. Дополнительные сведения см. в разделе [/errorReport (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Необязательный параметр `Int32`.<br /><br /> Задает размер разделов в выходном файле. Дополнительные сведения см. в разделе [/filealign (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, указывает абсолютный путь к файлу в выходных данных компилятора. Если `false`, указывает имя файла. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [/fullpaths (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает имя контейнера криптографического ключа. Дополнительные сведения см. в разделе [/keycontainer (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Задает имя файла, содержащего криптографический ключ. Дополнительные сведения см. в разделе [/keyfile (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Необязательный параметр `String` .<br /><br /> Задает используемую версию языка. Дополнительные сведения см. в разделе [/langversion (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Необязательные <xref:Microsoft.Build.Framework.ITaskItem>`[]` параметр.<br /><br /> Создает ссылку на [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ресурсов в выходной файл; файл ресурса не помещается в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр может иметь дополнительные записи метаданных с именем `LogicalName` и `Access`. `LogicalName` соответствует `identifier` параметр `/linkresource` Переключение, и `Access` соответствует `accessibility-modifier` параметр. Дополнительные сведения см. в разделе [/linkresource (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Необязательный параметр `String` .<br /><br /> Указывает расположение `Main` метод. Дополнительные сведения см. в разделе [/Main (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Необязательный параметр `String` .<br /><br /> Задает имя сборки, которая будет частью данный модуль.|  
|`NoConfig`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, указывает компилятору не компилировать с использованием файла csc.rsp. Дополнительные сведения см. в разделе [/noconfig (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, отключает вывод компилятора баннерной информации. Дополнительные сведения см. в разделе [/nologo (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, запрещает импорт библиотеки mscorlib.dll, которая определяет все пространство имен System. Используйте этот параметр, если нужно определить или создать собственное пространство имен System и объекты. Дополнительные сведения см. в разделе [/nostdlib (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, не включать манифест Win32 по умолчанию.|  
|`Optimize`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, включает оптимизацию. Если `false`, отключает оптимизацию. Дополнительные сведения см. в разделе [/ optimize (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Необязательные `String` выходной параметр.<br /><br /> Задает имя выходного файла. Дополнительные сведения см. в разделе [/out (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Необязательный параметр `String` .<br /><br /> Указывает имя файла отладочной информации. Имя по умолчанию — имя выходного файла с расширением .pdb.|  
|`Platform`|Необязательный параметр `String` .<br /><br /> Указывает целевую платформу процессора для выходного файла. Этот параметр может иметь значение `x86`, `x64`, или `anycpu`. Значение по умолчанию — `anycpu`. Дополнительные сведения см. в разделе [/Platform (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Необязательные <xref:Microsoft.Build.Framework.ITaskItem>`[]` параметр.<br /><br /> Запускает задание импортировать сведения об открытых типах из заданных элементов в текущий проект. Дополнительные сведения см. в разделе [/Reference (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Можно указать [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ссылку в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] добавляя метаданные `Aliases` с исходным элементом «Ссылка». Например, для которого задается псевдоним «LS1» в следующей командной строке CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> следует использовать:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Необязательные <xref:Microsoft.Build.Framework.ITaskItem>`[]` параметр.<br /><br /> Внедряет [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ресурсов в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр может иметь дополнительные записи метаданных с именем `LogicalName` и `Access`. `LogicalName` соответствует `identifier` параметр `/resource` Переключение, и `Access` соответствует `accessibility-modifier` параметр. Дополнительные сведения см. в разделе [/Resource (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Необязательный параметр `String` .<br /><br /> Задает файл ответов, содержащий команды для данной задачи. Дополнительные сведения см. в разделе [@ (указание файла ответа)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Необязательные <xref:Microsoft.Build.Framework.ITaskItem>`[]` параметр.<br /><br /> Указывает один или несколько [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] исходные файлы.|  
|`TargetType`|Необязательный параметр `String` .<br /><br /> Задает формат выходного файла. Этот параметр может иметь значение `library`, которого создается библиотека кода, `exe`, которой создается консольное приложение, `module`, который создает модуль, или `winexe`, создающем программы Windows. Значение по умолчанию — `library`. Дополнительные сведения см. в разделе [/Target (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, обрабатывать все предупреждения как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Необязательный параметр `Boolean` .<br /><br /> Указывает, что задаче использовать в внутрипроцессный объект компилятора, если он доступен. Используется только в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Необязательный параметр `Boolean` .<br /><br /> Журналы скомпилированный код с использованием кодировки UTF-8. Дополнительные сведения см. в разделе [/utf8output (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Необязательный параметр `Int32`.<br /><br /> Задает уровень предупреждений компилятора для отображения. Дополнительные сведения см. в разделе [/ warn (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Этот параметр переопределяет `TreatWarningsAsErrors` параметр.|  
|`WarningsNotAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Этот параметр полезен, только если `TreatWarningsAsErrors` параметр имеет значение `true`.|  
|`Win32Icon`|Необязательный параметр `String` .<br /><br /> Внедряет ICO-файл в сборку, которая придает выходному файлу требуемый вид в проводнике. Дополнительные сведения см. в разделе [/win32icon (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Необязательный параметр `String` .<br /><br /> Задает манифест Win32 для включения.|  
|`Win32Resource`|Необязательный параметр `String` .<br /><br /> Вставляет файл ресурсов (RES-файл) Win32 в выходной файл. Дополнительные сведения см. в разделе [/win32res (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров эта задача наследует параметры от `Microsoft.Build.Tasks.ManagedCompiler` класс, унаследованный от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension> класс, который наследует от <xref:Microsoft.Build.Utilities.ToolTask> класса. Список этих параметров и их описание см. в разделе [базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере используется `Csc` задач для создания исполняемого файла из исходных файлов в `Compile` коллекции элементов.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)