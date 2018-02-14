---
title: "Задача MarkupCompilePass1 | Документация Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ce65ca299bf8d43aa1ae22ee2c1bd0cf5300b68d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="markupcompilepass1-task"></a>Задача MarkupCompilePass1
Задача <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> преобразует нелокализуемые файлы проекта [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в скомпилированный двоичный формат.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит полный список файлов, созданных задачей <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Необязательный параметр типа **Boolean**.<br /><br /> Указывает, следует ли запускать задачу в отдельном <xref:System.AppDomain>. Если этот параметр возвращает **false**, задача выполняется в том же <xref:System.AppDomain>, что и [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]. Это позволяет выполнить задачу быстрее. Если этот параметр возвращает значение **true**, то задача выполняется во втором <xref:System.AppDomain>, который изолирован от [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] и работает медленнее.|  
|`ApplicationMarkup`|Необязательный параметр **ITaskItem[]**.<br /><br /> Задает имя файла определения приложения [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`AssembliesGeneratedDuringBuild`|Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые изменяются в процессе сборки. Например, решение [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] может содержать один проект, который ссылается на выходные данные компиляции другого проекта. В этом случае выходные данные компиляции второго проекта можно добавить в параметр **AssembliesGeneratedDuringBuild**.<br /><br /> Примечание. Параметр **AssembliesGeneratedDuringBuild** должен содержать ссылки на полный набор сборок, созданных решением сборки.|  
|`AssemblyName`|Обязательный параметр **string**.<br /><br /> Задает короткое имя сборки, которая создается для проекта. Например, если проект создает исполняемый файл [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] с именем **WinExeAssembly.exe**, то параметр **AssemblyName** имеет значение **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Необязательный параметр типа **String**.<br /><br /> Задает маркер открытого ключа для сборки.|  
|`AssemblyVersion`|Необязательный параметр типа **String**.<br /><br /> Задает номер версии сборки.|  
|`ContentFiles`|Необязательный параметр **ITaskItem[]**.<br /><br /> Задает список независимых файлов содержимого.|  
|`DefineConstants`|Необязательный параметр типа **String**.<br /><br /> Указывает, что текущее значение **DefineConstants** сохраняется, что влияет на создание конечной сборки. Изменение этого параметра может повлечь изменение общего API в конечной сборке и отразиться на компиляции файлов [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)], ссылающихся на локальные типы.|  
|`ExtraBuildControlFiles`|Необязательный параметр **ITaskItem[]**.<br /><br /> Задает список файлов, определяющих, выполняется ли перестройка при повторном запуске задачи <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. Перестройка активируется при изменении одного из этих файлов.|  
|`GeneratedBamlFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит список созданных файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`GeneratedCodeFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит список созданных файлов управляемого кода.|  
|`GeneratedLocalizationFiles`|Необязательный параметр вывода **ITaskItem[]**.<br /><br /> Содержит список файлов локализации, созданных для каждого локализуемого [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] файла XAML.|  
|`HostInBrowser`|Необязательный параметр типа **String**.<br /><br /> Определяет, является ли созданная сборка [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Допустимые значения: **true** и **false**. Если присвоено значение**true**, создается код поддержки размещения в браузере.|  
|`KnownReferencePaths`|Необязательный параметр типа **String[]**.<br /><br /> Задает ссылки на сборки, которые не изменяются в процессе сборки. Сюда включаются сборки, расположенные в [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], в каталоге установки [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] и т. д.|  
|`Language`|Обязательный параметр **string**.<br /><br /> Задает управляемый язык, который поддерживает компилятор. Допустимые значения: **C#**, **VB**, **JScript** и **C++**.|  
|`LanguageSourceExtension`|Необязательный параметр типа **String**.<br /><br /> Задает расширение, которое добавляется к расширению созданного файла управляемого кода:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Если для параметра **LanguageSourceExtension** не задано какое-либо определенное значение, используется стандартное расширение исходного файла для языка: **VB** для [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **CSHARP** для [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Необязательный параметр типа **String**.<br /><br /> Указывает, как создать сведения о локализации для каждого исходного файла [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Допустимые значения: **None**, **CommentsOnly** и **All**.|  
|`OutputPath`|Обязательный параметр **string**.<br /><br /> Указывает каталог, в котором создаются файлы управляемого кода и двоичные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputType`|Обязательный параметр **string**.<br /><br /> Задает тип сборки, которая создается проектом. Допустимые значения: **winexe**, **exe**, **library** и **netmodule**.|  
|`PageMarkup`|Необязательный параметр **ITaskItem[]**.<br /><br /> Задает список обрабатываемых файлов [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`References`|Необязательный параметр **ITaskItem[]**.<br /><br /> Указывает список содержащихся в файлах ссылок на сборки, которые содержат типы, используемые в файлах [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`RequirePass2ForMainAssembly`|Необязательный параметр вывода типа **Boolean**.<br /><br /> Указывает, содержит ли проект нелокализуемые файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] со ссылками на локальные типы, внедренные в основную сборку.|  
|`RequirePass2ForSatelliteAssembly`|Необязательный параметр вывода типа **Boolean**.<br /><br /> Указывает, содержит ли проект локализуемые файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] со ссылками на локальные типы, внедренные в основную сборку.|  
|`RootNamespace`|Необязательный параметр типа **String**.<br /><br /> Задает корневое пространство имен для классов, которые находятся внутри проекта. **RootNamespace** также используется как пространство имен по умолчанию для созданного файла управляемого кода, если соответствующий файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] не содержит атрибут `x:Class`.|  
|`SourceCodeFiles`|Необязательный параметр **ITaskItem[]**.<br /><br /> Задает список файлов кода для текущего проекта. В этот список не входят файлы управляемого кода, созданные для определенного языка.|  
|`UICulture`|Необязательный параметр типа **String**.<br /><br /> Задает вспомогательную сборку для языка и региональных параметров пользовательского интерфейса, в которую внедряются созданные двоичные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Если значение для **UICulture** не задано, созданные двоичные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] внедряются в основную сборку.|  
|`XAMLDebuggingInformation`|Необязательный параметр типа **Boolean**.<br /><br /> Если он имеет значение **true**, для помощи в отладке создается диагностическая информация, которая помещается в скомпилированный элемент [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
  
## <a name="remarks"></a>Примечания  
 Задача <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> обычно компилирует [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичный формат и создает файлы кода. Если файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] содержит ссылки на типы, заданные в том же самом проекте, его компиляция в двоичный формат откладывается **MarkupCompilePass1** до второго этапа компиляции разметки (**MarkupCompilePass2**). Компиляция таких файлов должна быть отложена, так как им необходимо дождаться компиляции локально определенных типов, на которые имеются ссылки. Однако, если в файле [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] есть атрибут `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> создает для него языковую версию файла кода.  
  
 Файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] можно локализовать, если в нем содержатся элементы, использующие атрибут `x:Uid`:  
  
```xml  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ссылается на локально определенный тип, когда в нем объявляется пространство имен [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)], использующее значение `clr-namespace` для ссылки на пространство имен в текущем проекте:  
  
```xml  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Если какой-либо файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] можно локализовать или он содержит ссылки на локально определенный тип, необходим второй этап компиляции разметки. Для этого требуется выполнить [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), а затем — [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как преобразовать три файла `Page` [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в файлы двоичного формата. `Page1` содержит ссылку на тип `Class1`, который находится в корневом пространстве имен проекта и не преобразуется в файлы двоичного формата на данном этапе компиляции разметки. Вместо этого выполняется [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), а затем — [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Общие сведения о приложениях браузера WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)