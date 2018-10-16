---
title: Преобразования MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce1d0b63518fb48636fca38b2788eea2d0c189a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223710"
---
# <a name="msbuild-transforms"></a>Преобразования MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Преобразование — это однозначное преобразование одного списка элементов в другой. Помимо возможности преобразования списков элементов в проекте, преобразование позволяет целевому объекту определить прямое сопоставление входных и выходных данных. Этот раздел описывает преобразования и то, как [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] использует их для более эффективной сборки проектов.  
  
## <a name="transform-modifiers"></a>Модификаторы преобразования  
 Преобразования не являются произвольными, они ограничены специальным синтаксисом, в котором все модификаторы преобразования должны иметь формат %(*имя_метаданных_элемента*). Метаданные элементов можно использовать в качестве модификаторов преобразования. Сюда входят стандартные метаданные элементов, назначаемые каждому элементу при создании. Список стандартных метаданных элементов см. в статье [Стандартные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md).  
  
 В следующем примере список файлов RESX преобразуется в список файлов RESOURCES. Модификатор преобразования %(filename) указывает, что каждый файл RESOURCES имеет то же имя, что и соответствующий файл RESX.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Вы можете указать настраиваемый разделитель для преобразованного списка элементов точно так же, как и для стандартного списка элементов. Например, чтобы разделить преобразованный список элементов с помощью запятой (,), а не используемой по умолчанию точки с запятой (;), используйте следующий XML-код.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Например, если список элементов @(RESXFile) содержит элементы `Form1.resx`, `Form2.resx` и `Form3.resx`, преобразованный список будет содержать выходные данные `Form1.resources`, `Form2.resources` и `Form3.resources`.  
  
## <a name="using-multiple-modifiers"></a>Использование нескольких модификаторов  
 Выражение преобразования может содержать несколько модификаторов, которые можно объединять в любом порядке, кроме того, они могут повторяться. В следующем примере изменяется имя каталога, содержащего файлы, однако файлы сохраняют исходное имя и расширение.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Например, если список элементов `RESXFile` содержит элементы `Project1\Form1.resx`, `Project1\Form2.resx` и `Project1\Form3.text`, преобразованный список будет содержать выходные данные `Toolset\Form1.resx`, `Toolset\Form2.resx` и `Toolset\Form3.text`.  
  
## <a name="dependency-analysis"></a>Анализ зависимостей  
 Преобразование обеспечивает однозначное сопоставление между преобразованным и исходным списками элементов. Таким образом, если целевой объект создает выходные данные, полученные путем преобразования входных файлов, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может проанализировать метки времени входных и выходных данных и решить, следует ли пропустить целевой объект, выполнить его сборку или частично перестроить.  
  
 В [задаче Copy](../msbuild/copy-task.md) в следующем примере каждый файл в списке элементов `BuiltAssemblies` сопоставляется с файлом в папке назначения задачи, указанной с помощью преобразования в атрибуте `Outputs`. Если изменяется файл в списке элементов `BuiltAssemblies`, задача `Copy` будет выполняться только для измененного файла, а все остальные файлы будут пропущены. Дополнительные сведения об анализе зависимостей и использовании преобразований см. в разделе [Практическое руководство. Инкрементная сборка](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 Следующий пример показывает файл проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], использующий преобразования. В этом примере предполагается, что в каталоге c:\sub0\sub1\sub2\sub3 имеется только один XSD-файл, а рабочим каталогом является c:\sub0.  
  
### <a name="code"></a>Код  
  
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
  
### <a name="comments"></a>Комментарии  
 В этом примере формируются следующие данные:  
  
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
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Практическое руководство. Инкрементное построение](../msbuild/how-to-build-incrementally.md)



