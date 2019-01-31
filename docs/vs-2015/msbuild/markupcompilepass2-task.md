---
title: Задача MarkupCompilePass2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c31551541bc949a98ec2dd7a15da5a86b36d21
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777096"
---
# <a name="markupcompilepass2-task"></a>Задача MarkupCompilePass2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Задача <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> выполняет второй проход компиляции разметки на файлах [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)], которые ссылаются на типы в том же проекте.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Необязательный параметр **Boolean** .<br /><br /> Указывает, следует ли запускать задачу в отдельном <xref:System.AppDomain>. Если этот параметр возвращает **false**, задача выполняется в том же <xref:System.AppDomain>, что и [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)]. Это позволяет выполнить задачу быстрее. Если этот параметр возвращает значение **true**, то задача выполняется во втором <xref:System.AppDomain>, который изолирован от [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] и работает медленнее.|  
|`AssembliesGeneratedDuringBuild`|Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые изменяются в процессе сборки. Например, решение [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] может содержать один проект, который ссылается на выходные данные компиляции другого проекта. В этом случае выходные данные компиляции второго проекта можно добавить в **AssembliesGeneratedDuringBuild**.<br /><br /> Примечание. Элемент **AssembliesGeneratedDuringBuild** должен содержать ссылки на полный набор сборок, созданных решением сборки.|  
|`AssemblyName`|Обязательный параметр **string**.<br /><br /> Задает короткое имя сборки, которая создается для проекта. Например, если проект создает исполняемый файл [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] с именем **WinExeAssembly.exe**, то параметр **AssemblyName** имеет значение **WinExeAssembly**.|  
|`GeneratedBaml`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит список созданных файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
|`KnownReferencePaths`|Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые не изменяются в процессе сборки. Сюда включаются сборки, расположенные в [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)], в каталоге установки [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] и т. д.|  
|`Language`|Обязательный параметр **string**.<br /><br /> Задает управляемый язык, который поддерживает компилятор. Допустимые значения: **C#**, **VB**, **JScript** и **C++**.|  
|`LocalizationDirectivesToLocFile`|Необязательный параметр типа **String**.<br /><br /> Указывает, как создать сведения о локализации для каждого исходного файла [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]. Допустимые значения: **None**, **CommentsOnly** и **All**.|  
|`OutputPath`|Обязательный параметр **string**.<br /><br /> Указывает каталог, в котором сохраняются созданные файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] в двоичном формате.|  
|`OutputType`|Обязательный параметр **string**.<br /><br /> Задает тип сборки, которая создается проектом. Допустимые значения: **winexe**, **exe**, **library** и **netmodule**.|  
|`References`|Необязательный параметр **ITaskItem[]**.<br /><br /> Указывает список содержащихся в файлах ссылок на сборки, которые содержат типы, используемые в файлах [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]. Одна ссылка указывает на сборку, созданную задачей <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, которая должна выполняться перед задачей <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Необязательный параметр типа **String**.<br /><br /> Задает корневое пространство имен для классов, которые находятся внутри проекта. **RootNamespace** также используется как пространство имен по умолчанию для созданного файла управляемого кода, если соответствующий файл [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] не содержит атрибут `x:Class`.|  
|`XAMLDebuggingInformation`|Необязательный параметр **Boolean** .<br /><br /> Если он имеет значение **true**, для помощи в отладке создается диагностическая информация, которая помещается в скомпилированный элемент [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 Прежде чем выполнять **MarkupCompilePass2**, необходимо создать временную сборку, содержащую используемые в файлах [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] типы, так как компиляция разметки для этих файлов откладывается на второй проход. Чтобы создать эту временную сборку, запустите задачу **GenerateTemporaryTargetAssembly**.  
  
 Ссылка на созданную временную сборку передается в задачу <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> при ее запуске. Это позволяет скомпилировать в двоичный формат файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)], компиляция которых была отложена при первом проходе компиляции разметки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать задачу <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> для выполнения второго прохода компиляции.  
  
```  
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
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Общие сведения о приложениях браузера WPF XAML](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
