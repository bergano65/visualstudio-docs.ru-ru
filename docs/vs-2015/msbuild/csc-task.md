---
title: Задача Csc | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0dd27fe64982e77872e37ec01dbdb71a0a141ae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694104"
---
# <a name="csc-task"></a>Задача Csc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Использует программу-оболочку для файла CSC.exe и создает исполняемые файлы (EXE-файлы), библиотеки динамической компоновки (DLL-файлы) или модули кода (NETMODULE-файлы). Дополнительные сведения о программе CSC.EXE см. в разделе [Параметры компилятора C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `Csc` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Необязательный параметр `String[]` .<br /><br /> Задает дополнительные каталоги для поиска ссылок. Дополнительные сведения см. в разделе [/lib (параметры компилятора C#)](https://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Необязательный параметр `String` .<br /><br /> Задает один или несколько модулей, которые должны быть частью сборки. Дополнительные сведения см. в разделе [/addmodule (параметры компилятора C#)](https://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, то компилируется код, в котором используется ключевое слово [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Дополнительные сведения см. в разделе [/unsafe (параметры компилятора C#)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Необязательный параметр `String` .<br /><br /> Задает файл конфигурации приложения, содержащий параметры привязки сборки.|  
|`BaseAddress`|Необязательный параметр `String` .<br /><br /> Указывает предпочтительный базовый адрес для загрузки DLL. Базовый адрес по умолчанию для библиотеки DLL задается в среде CLR [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Дополнительные сведения см. в разделе [/baseaddress (параметры компилятора C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Необязательный параметр `Boolean` .<br /><br /> Указывает, должны ли целочисленные арифметические операции, вызывающие переполнение типа данных, вызывать исключение во время выполнения. Дополнительные сведения см. в разделе [/checked (параметры компилятора C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Необязательный параметр `Int32` .<br /><br /> Задает кодовую страницу, которая будет использоваться для всех файлов исходного кода при компиляции. Дополнительные сведения см. в разделе [/codepage (параметры компилятора C#)](https://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Необязательный параметр `String` .<br /><br /> Задает тип отладки. `DebugType` может иметь значение `full`или `pdbonly`. По умолчанию задано значение `full`, разрешающее подключение отладчика к исполняемой программе. Значение `pdbonly` разрешает отладку исходного кода при запуске программы в отладчике, но при этом ассемблерный код отображается только при подключении исполняемой программы к отладчику.<br /><br /> Этот параметр переопределяет параметр `EmitDebugInformation`.<br /><br /> Дополнительные сведения см. в разделе [/debug (параметры компилятора C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Необязательный параметр `String` .<br /><br /> Определяет символы препроцессора. Дополнительные сведения см. в разделе [/define (параметры компилятора C#)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` предписывает создание полностью подписанной сборки. Значение `false` предписывает лишь поместить в сборку открытый ключ.<br /><br /> Этот параметр не оказывает никакого эффекта, если не используется вместе с параметром `KeyFile` или `KeyContainer`.<br /><br /> Дополнительные сведения см. в разделе [/delaysign (параметры компилятора C#)](https://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые следует отключить. Дополнительные сведения см. в разделе [/nowarn (параметры компилятора C#)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Необязательный параметр `String` .<br /><br /> Обрабатывает комментарии к документации в XML-файл. Дополнительные сведения см. в разделе [/doc (параметры компилятора C#)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, задача генерирует отладочную информацию и помещает ее в файл базы данных программы (PDB-файл). Если задано значение `false`, задача не генерирует отладочную информацию. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [/debug (параметры компилятора C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Необязательный параметр `String` .<br /><br /> Предоставляет удобный способ для сообщения о внутренней ошибке C# в корпорацию Майкрософт. Этот параметр может иметь значение `prompt`, `send` или `none`. Если установлено значение `prompt`, в случае внутренней ошибки компилятора будет выведено сообщение с предложением отправить электронный отчет об ошибке в корпорацию Майкрософт. Если установлено значение `send`, сообщение об ошибке отправляется автоматически. Если установлено значение `none`, отчет об ошибке выводится только в текстовых выходных данных компилятора. Значение по умолчанию — `none`. Дополнительные сведения см. в разделе [/errorreport (параметры компилятора C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Необязательный параметр `Int32` .<br /><br /> Задает размер разделов в выходном файле. Дополнительные сведения см. в разделе [/filealign (параметры компилятора C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, то в выходных данных компилятора задается абсолютный путь к файлу. Если установлено значение `false`, задается имя файла. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [/fullpaths (параметры компилятора C#)](https://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает имя контейнера криптографического ключа. Дополнительные сведения см. в разделе [/keycontainer (параметры компилятора C#)](https://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Задает имя файла, содержащего криптографический ключ. Дополнительные сведения см. в разделе [/keyfile (параметры компилятора C#)](https://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Необязательный параметр `String` .<br /><br /> Задает используемую версию языка. Дополнительные сведения см. в разделе [/langversion (параметры компилятора C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Создает ссылку на ресурс [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] в выходном файле; файл ресурса не помещается в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр, могут иметь необязательные метаданные `LogicalName` и `Access`. `LogicalName` соответствует аргументу `identifier` параметра `/linkresource`, а `Access` соответствует аргументу `accessibility-modifier`. Дополнительные сведения см. в разделе [/linkresource (параметры компилятора C#)](https://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Необязательный параметр `String` .<br /><br /> Указывает расположение метода `Main`. Дополнительные сведения см. в разделе [/main (параметры компилятора C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Необязательный параметр `String` .<br /><br /> Задает имя сборки, частью которой будет этот модуль.|  
|`NoConfig`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` предписывает компилятору не использовать файл CSC.RSP. Дополнительные сведения см. в разделе [/noconfig (параметры компилятора C#)](https://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, отображение заголовка компилятора отключается. Дополнительные сведения см. в разделе [/nologo (параметры компилятора C#)](https://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` отключает импорт библиотеки mscorlib.dll, определяющей все пространство имен System. Используйте этот параметр, если вы хотите определить или создать собственное пространство имен System и соответствующие объекты. Дополнительные сведения см. в разделе [/nostdlib (параметры компилятора C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Необязательный параметр `Boolean` .<br /><br /> Если значение `true`, манифест Win32 по умолчанию не включается.|  
|`Optimize`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` включает оптимизации. Значение `false` отключает оптимизации. Дополнительные сведения см. в разделе [/optimize (параметры компилятора C#)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Необязательный выходной параметр `String`.<br /><br /> Задает имя выходного файла. Дополнительные сведения см. в разделе [/out (параметры компилятора C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Необязательный параметр `String` .<br /><br /> Задает имя файла отладочной информации. По умолчанию используется имя файла выходных данных с расширением PDB.|  
|`Platform`|Необязательный параметр `String` .<br /><br /> Указывает целевую платформу процессора для выходного файла. Этот параметр может иметь значение `x86`, `x64` или `anycpu`. Значение по умолчанию — `anycpu`. Дополнительные сведения см. в разделе [/platform (параметры компилятора C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Вызывает импорт задачей информации об открытых типах из заданных элементов в текущий проект. Дополнительные сведения см. в разделе [/reference (параметры компилятора C#)](https://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Вы можете задать псевдоним ссылки [!INCLUDE[csprcs](../includes/csprcs-md.md)] в файле [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], добавив метаданные `Aliases` к исходному элементу Reference. Например, пусть требуется установить псевдоним LS1 в следующей командной строке CSC.<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Для этого используется следующий код.<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Внедряет ресурс [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр, могут иметь необязательные метаданные `LogicalName` и `Access`. `LogicalName` соответствует аргументу `identifier` параметра `/resource`, а `Access` соответствует аргументу `accessibility-modifier`. Дополнительные сведения см. в разделе [/resource (параметры компилятора C#)](https://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Необязательный параметр `String` .<br /><br /> Задает файл ответов, содержащий команды для этой задачи. Дополнительные сведения см. в документации синтаксиса [@ (указание файла ответа)](https://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает один или несколько файлов исходного кода [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`TargetType`|Необязательный параметр `String` .<br /><br /> Задает формат выходного файла. Этот параметр может принимать одно из следующих значений: `library` (создается библиотека кода), `exe` (создается консольное приложение), `module` (создается модуль) или `winexe` (создается программа Windows). Значение по умолчанию — `library`. Дополнительные сведения см. в разделе [/target (параметры компилятора C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр равен `true`, все предупреждения обрабатываются как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Необязательный параметр `Boolean` .<br /><br /> Предписывает задаче использовать внутрипроцессный объект компилятора, если он доступен. Используется только в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Необязательный параметр `Boolean` .<br /><br /> Регистрирует выходные данные компилятора в кодировке UTF-8. Дополнительные сведения см. в разделе [/utf8output (параметры компилятора C#)](https://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Необязательный параметр `Int32` .<br /><br /> Задает уровень предупреждений, которые должны отображаться компилятором. Дополнительные сведения см. в разделе [/warn (параметры компилятора C#)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Этот параметр переопределяет параметр `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Необязательный параметр `String` .<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [/warnaserror (параметры компилятора C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Этот параметр имеет смысл только в том случае, если для параметра `TreatWarningsAsErrors` задано значение `true`.|  
|`Win32Icon`|Необязательный параметр `String` .<br /><br /> Вставляет ICO-файл в сборку, которая придает выходному файлу необходимый вид в проводнике. Дополнительные сведения см. в разделе [/win32icon (параметры компилятора C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Необязательный параметр `String` .<br /><br /> Задает манифест Win32, который требуется включить.|  
|`Win32Resource`|Необязательный параметр `String` .<br /><br /> Вставляет файл ресурсов Win32 (RES-файл) в выходной файл. Дополнительные сведения см. в разделе [/win32res (параметры компилятора C#)](https://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса `Microsoft.Build.Tasks.ManagedCompiler`, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, наследующего от класса <xref:Microsoft.Build.Utilities.ToolTask>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере задача `Csc` используется для компиляции исполняемого файла из исходных файлов в коллекции элементов `Compile`.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
