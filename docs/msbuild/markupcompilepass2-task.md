---
title: Задача MarkupCompilePass2 | Документация Майкрософт
description: Сведения об использовании задачи MarkupCompilePass2 в MSBuild для выполнения второго прохода компиляции разметки для файлов XAML, которые ссылаются на типы, определенные в этом же проекте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7425e0342974c3b000486f57227f768aac47b9ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966179"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 - задача

Задача <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> выполняет второй проход компиляции разметки на файлах XAML, которые ссылаются на типы в том же проекте.

## <a name="task-parameters"></a>Параметры задачи

| Параметр | Описание |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Необязательный параметр **Boolean** .<br /><br /> Указывает, следует ли запускать задачу в отдельном <xref:System.AppDomain>. Если этот параметр возвращает **false**, задача выполняется в том же <xref:System.AppDomain>, что и MSBuild. Это позволяет выполнить задачу быстрее. Если этот параметр возвращает значение **true**, то задача выполняется во втором <xref:System.AppDomain>, который изолирован от MSBuild и работает медленнее. |
| `AssembliesGeneratedDuringBuild` | Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые изменяются в процессе сборки. Например, решение Visual Studio может содержать один проект, который ссылается на выходные данные компиляции другого проекта. В этом случае выходные данные компиляции второго проекта можно добавить в **AssembliesGeneratedDuringBuild**.<br /><br /> Примечание. Элемент **AssembliesGeneratedDuringBuild** должен содержать ссылки на полный набор сборок, созданных решением сборки. |
| `AssemblyName` | Обязательный параметр **String**.<br /><br /> Задает короткое имя сборки, которая создается для проекта. Например, если проект создает исполняемый файл с именем *WinExeAssembly.exe*, то параметр **AssemblyName** имеет значение **WinExeAssembly**. |
| `GeneratedBaml` | Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит список созданных файлов в двоичном формате XAML. |
| `KnownReferencePaths` | Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые не изменяются в процессе сборки. Сюда включаются сборки, расположенные в глобальном кэше сборок, в каталоге установки .NET и т. д. |
| `Language` | Обязательный параметр **String**.<br /><br /> Задает управляемый язык, который поддерживает компилятор. Допустимые значения: **C#**, **VB**, **JScript** и **C++**. |
| `LocalizationDirectivesToLocFile` | Необязательный параметр **String** .<br /><br /> Указывает, как создать сведения о локализации для каждого исходного файла XAML. Допустимые значения: **None**, **CommentsOnly** и **All**. |
| `OutputPath` | Обязательный параметр **String**.<br /><br /> Указывает каталог, в котором сохраняются созданные файлы XAML в двоичном формате. |
| `OutputType` | Обязательный параметр **String**.<br /><br /> Задает тип сборки, которая создается проектом. Допустимые значения: **winexe**, **exe**, **library** и **netmodule**. |
| `References` | Необязательный параметр **ITaskItem[]** .<br /><br /> Указывает список содержащихся в файлах ссылок на сборки, которые содержат типы, используемые в файлах XAML. Одна ссылка указывает на сборку, созданную задачей <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, которая должна выполняться перед задачей <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Необязательный параметр **String** .<br /><br /> Задает корневое пространство имен для классов, которые находятся внутри проекта. **RootNamespace** также используется как пространство имен по умолчанию для созданного файла управляемого кода, если соответствующий файл XAML не содержит атрибут `x:Class`. |
| `XAMLDebuggingInformation` | Необязательный параметр **Boolean** .<br /><br /> Если он имеет значение **true**, для помощи в отладке создается диагностическая информация, которая помещается в скомпилированный элемент XAML. |

## <a name="remarks"></a>Комментарии

Прежде чем выполнять **MarkupCompilePass2**, необходимо создать временную сборку, содержащую используемые в файлах XAML типы, так как компиляция разметки для этих файлов откладывается на второй проход. Чтобы создать эту временную сборку, запустите задачу **GenerateTemporaryTargetAssembly**.

Ссылка на созданную временную сборку передается в задачу <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> при ее запуске. Это позволяет скомпилировать в двоичный формат файлы XAML, компиляция которых была отложена при первом проходе компиляции разметки.

## <a name="example"></a>Пример

В следующем примере показано, как использовать задачу <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> для выполнения второго прохода компиляции.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах WPF для MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочник по задачам MSBuild](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Общие сведения о приложениях браузера WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
