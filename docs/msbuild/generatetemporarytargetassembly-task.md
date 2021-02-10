---
title: Задача GenerateTemporaryTargetAssembly | Документация Майкрософт
description: Используйте задачу GenerateTemporaryTargetAssembly MSBuild для создания сборки, если проект ссылается на тип, объявленный локально.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4a41a5cbecea69d4843cbd70479a604f91b2218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914739"
---
# <a name="generatetemporarytargetassembly-task"></a>Задача GenerateTemporaryTargetAssembly

Задача <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> создает сборку, если по меньшей мере одна страница XAML в проекте ссылается на тип, объявленный в этом проекте локально. Созданная сборка удаляется после успешного или неудачного завершения процесса сборки.

## <a name="task-parameters"></a>Параметры задачи

| Параметр | Описание |
|--------------------------| - |
| `AssemblyName` | Обязательный параметр **String**.<br /><br /> Задает короткое имя сборки, которая создается для проекта, и которое также используется для временно создаваемой конечной сборки. Например, если проект создает исполняемый файл Windows с именем *WinExeAssembly.exe*, параметр **AssemblyName** имеет значение **WinExeAssembly**. |
| `CompileTargetName` | Обязательный параметр **String**.<br /><br /> Указывает имя целевого объекта MSBuild, который используется для создания сборок из файлов исходного кода. Для параметра **CompileTargetName** обычно используется значение **CoreCompile**. |
| `CompileTypeName` | Обязательный параметр **String**.<br /><br /> Задает тип компиляции, которую выполняет целевой объект, указанный в параметре **CompileTargetName**. Для целевого объекта **CoreCompile** этот параметр имеет значение **Compile**. |
| `CurrentProject` | Обязательный параметр **String**.<br /><br /> Указывает полный путь к файлу проекта MSBuild для проекта, которому требуется временная конечная сборка. |
| `GeneratedCodeFiles` | Необязательный параметр **ITaskItem[]** .<br /><br /> Указывает список файлов управляемого кода для определенного языка, созданных задачей [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md). |
| `IntermediateOutputPath` | Обязательный параметр **String**.<br /><br /> Указывает каталог, в котором создана временная конечная сборка. |
| `MSBuildBinPath` | Обязательный параметр **String**.<br /><br /> Указывает расположение файла *MSBuild.exe*, который необходим для компиляции временной конечной сборки. |
| `ReferencePath` | Необязательный параметр **ITaskItem[]** .<br /><br /> Указывает список сборок (имя файла и путь), на которые ссылаются все типы, скомпилированные во временной конечной сборке. |
| `ReferencePathTypeName` | Обязательный параметр **String**.<br /><br /> Задает параметр, используемый параметром целевого объекта компиляции (**CompileTargetName**), который задает список ссылок на сборку (**ReferencePath**). Мы рекомендуем использовать значение **ReferencePath**. |

## <a name="remarks"></a>Remarks

При первом проходе компиляции разметки, который выполняет процесс [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), файлы XAML компилируются в двоичный формат. Для этого компилятору требуется список сборок, на которые есть ссылки и которые содержат типы, используемые в файлах XAML. Но если файл XAML использует тип, который определен в том же проекте, соответствующая сборка для этого проекта не будет создана, пока не будет выполнена сборка проекта. Следовательно, ссылку на сборку во время первого прохода компиляции разметки предоставить невозможно.

Вместо этого **MarkupCompilePass1** откладывает преобразование файлов XAML, которые содержат ссылки на типы, определенные в том же проекте, до второй компиляции разметки, которую выполнит процесс [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). До момента выполнения **MarkupCompilePass2** создается временная сборка. Эта сборка содержит типы, используемые файлами XAML, компиляция разметки для которых была отложена. Ссылка на созданную сборку передается в **MarkupCompilePass2** при его запуске, чтобы он мог выполнить отложенную компиляцию файлов XAML в двоичный формат.

## <a name="example"></a>Пример

Следующий пример создает временную сборку, так как файл *Page1.xaml* содержит ссылку на тип, определенный в том же проекте.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Общие сведения о приложениях браузера WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
