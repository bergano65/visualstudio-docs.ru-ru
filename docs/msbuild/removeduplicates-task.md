---
title: "Задача RemoveDuplicates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RemoveDuplicates - задача"
  - "RemoveDuplicates - задача [MSBuild]"
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Задача RemoveDuplicates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Удаляет повторяющиеся элементы из указанной коллекции элементов.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `RemoveDuplicates`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Filtered`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит коллекцию элементов со всеми удаленными повторяющимися элементами.|  
|`Inputs`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Коллекция элементов, из которой нужно удалить повторяющиеся элементы.|  
  
## Заметки  
 Эта задача при сравнении не учитывает регистр, а также не сравнивает метаданные элемента при определении повторяющихся элементов.  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере показано использование задачи `RemoveDuplicates` для удаления повторяющихся элементов из коллекции элементов `MyItems`.  После завершения задачи коллекция элементов `FilteredItems` содержит один элемент.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)   
 [Задачи](../msbuild/msbuild-tasks.md)