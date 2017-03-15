---
title: "Практическое руководство. Очистка построения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "каталоги [платформа .NET Framework], для выходных элементов"
  - "Exec - задача [MSBuild]"
  - "MSBuild, чистка построения"
  - "результат, удаление элементов"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Практическое руководство. Очистка построения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При очистке построения все промежуточные и выходные файлы удаляются; остаются только файлы проекта и компонентов.  Затем из файлов проекта и компонентов можно строить новые экземпляры промежуточных и выходных файлов.  В предоставленной [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] библиотеке общих задач имеется задача [Exec](../msbuild/exec-task.md), с помощью которой можно выполнять системные команды.  Дополнительные сведения о библиотеке задач см. в разделе [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md).  
  
## Создание каталога для выходных элементов  
 По умолчанию EXE\-файл, созданный при компиляции проекта, помещается в тот же каталог, где находятся файлы проекта и исходные файлы.  Однако выходные элементы обычно создаются в отдельном каталоге.  
  
#### Создание каталога для выходных элементов  
  
1.  Чтобы определить расположение и имя каталога, используйте элемент `Property`.  Например, создайте каталог с именем `BuiltApp` в каталоге, содержащем файлы проекта и исходные файлы:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Если каталога не существует, можно создать его с помощью задачи [MakeDir](../msbuild/makedir-task.md).  Примеры.  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Удаление выходных элементов  
 Прежде чем создавать новые экземпляры промежуточных и выходных файлов, можно очистить все предыдущие экземпляры этих файлов.  Чтобы удалить с диска каталог и все содержащиеся в нем файлы и каталоги, используйте задачу [RemoveDir](../msbuild/removedir-task.md).  
  
#### Удаление каталога и всех содержащихся в нем файлов  
  
-   Чтобы удалить каталог, используйте задачу `RemoveDir`.  Примеры.  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Пример  
 В следующем примере кода проекта содержится новый целевой объект, `Clean`, в котором используется задача `RemoveDir` для удаления каталога и всех содержащихся в нем файлов и каталогов.  Кроме того, в этом примере целевым объектом `Compile` создается отдельный каталог для выходных файлов, которые удаляются при очистке построения.  
  
 `Compile` определен в качестве целевого объекта по умолчанию и используется автоматически, если не указаны другие целевые объекты.  Чтобы указать другой целевой объект, используйте ключ командной строки **\/target**.  Примеры.  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Ключ **\/target** можно сокращать до **\/t**, а также можно указывать несколько целевых объектов.  Например, чтобы использовать целевой объект `Clean`, а затем целевой объект `Compile`, введите:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задача Exec](../msbuild/exec-task.md)   
 [Задача MakeDir](../msbuild/makedir-task.md)   
 [Задача RemoveDir](../msbuild/removedir-task.md)   
 [Задача Csc](../msbuild/csc-task.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)