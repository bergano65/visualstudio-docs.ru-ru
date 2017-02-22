---
title: "Преобразования MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, преобразования"
  - "преобразования [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Преобразования MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Преобразование — это взаимнооднозначное превращение одного списка элементов в другой.  Помимо преобразования списков элементов в проекте, преобразования также позволяют целевому объекту определить прямое сопоставление входных и выходных данных.  В данном разделе описываются преобразования и способы их использования в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для эффективного построения проектов.  
  
## Модификаторы преобразований  
 Преобразования не выполняются произвольно, они ограничены определенным синтаксисом, в котором все модификаторы преобразований должны указываться в формате %\(*ItemMetaDataName*\).  В качестве модификаторов можно использовать метаданные элементов,  в том числе стандартные метаданные, которые присваиваются элементам при их создании.  Список стандартных метаданных элементов см. в разделе [Стандартные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md).  
  
 В приведенном ниже примере показано, как список файлов .resx преобразуется в список файлов .resources.  Модификатор преобразования %\(filename\) указывает, что каждый файл .resources должен иметь то же имя, что и соответствующий файл .resx.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Для преобразованного списка элементов можно задать пользовательский разделитель точно так же, как и для обычного списка элементов.  В следующем примере XML\-кода в качестве разделителя элементов преобразованного списка задается запятая \(,\), а не точка с запятой \(;\), используемая по умолчанию.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Например, если в списке элементов @\(RESXFile\) содержатся элементы `Form1.resx`, `Form2.resx` и `Form3.resx`, в преобразованном списке будут содержаться элементы `Form1.resources`, `Form2.resources` и `Form3.resources`.  
  
## Использование нескольких модификаторов  
 Выражение преобразования может содержать несколько модификаторов, которые можно указывать в произвольном порядке и повторять.  В следующем примере имя каталога, содержащего файлы, изменено, но файлы сохраняют исходное имя и расширение.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Например, если в списке элементов `RESXFile` содержатся элементы `Project1\Form1.resx`, `Project1\Form2.resx` и `Project1\Form3.text`, в преобразованном списке будут содержаться элементы `Toolset\Form1.resx`, `Toolset\Form2.resx` и `Toolset\Form3.text`.  
  
## Анализ зависимости  
 Преобразование обеспечивает взаимнооднозначное сопоставление между преобразованным списком элементов и исходным списком элементов.  Поэтому, если в целевом объекте создаются выходные файлы, полученные преобразованием входных файлов, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может проанализировать метки времени входных и выходных файлов и решить, следует ли пропустить, построить или частично перестроить целевой объект.  
  
 В приведенном ниже примере в задаче [Задача Copy](../msbuild/copy-task.md) каждый файл из списка элементов `BuiltAssemblies` сопоставляется с файлом из конечной папки задачи, указанной с помощью преобразования в атрибуте `Outputs`.  Если один из файлов в списке элементов `BuiltAssemblies` изменяется, задача `Copy` будет выполняться только для измененного файла, а все остальные файлы будут пропущены.  Дополнительные сведения об анализе зависимости и использовании преобразований см. в разделе [Практическое руководство. Инкрементное построение](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## Пример  
  
### Описание  
 В следующем примере показан файл проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], в котором используются преобразования.  В примере предполагается, что в каталоге c:\\sub0\\sub1\\sub2\\sub3 содержится только один XSD\-файл и используется рабочий каталог c:\\sub0.  
  
### Код  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### Комментарии  
 В результате выполнения примера получается следующий результат:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## См. также  
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Практическое руководство. Инкрементное построение](../msbuild/how-to-build-incrementally.md)