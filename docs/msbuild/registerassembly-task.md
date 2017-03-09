---
title: "Задача RegisterAssembly | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RegisterAssembly - задача"
  - "RegisterAssembly - задача [MSBuild]"
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача RegisterAssembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Считывание метаданных в указанной сборке и добавление необходимых записей в реестр, что позволяет клиентам COM прозрачно создавать классы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Поведение этой задачи аналогично, но не идентично поведению [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md).  
  
## Параметры  
 В следующей таблице описаны параметры задачи `RegisterAssembly`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Assemblies`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Сборки, регистрируемые с помощью COM.|  
|`AssemblyListFile`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Сведения о состоянии между выполнением задач `RegisterAssembly` и [UnregisterAssembly](../msbuild/unregisterassembly-task.md).  Это препятствует попытке задачи `UnregisterAssembly` отменить регистрацию сборки, которую не удалось зарегистрировать в задаче `RegisterAssembly`.|  
|`CreateCodeBase`|Необязательный параметр типа `Boolean`.<br /><br /> При значении `true` в реестре создается запись Codebase, задающая путь к файлу сборки, которая не устанавливается в глобальный кэш сборок.  Не следует указывать этот параметр, если впоследствии будет установлена сборка, регистрируемая в глобальном кэше сборок.|  
|`TypeLibFiles`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Библиотека типов, создаваемая из заданной сборки.  В созданной библиотеке типов содержатся определения доступных типов, заданных в сборке.  Библиотека типов создается, только если справедливо одно из следующих условий:<br /><br /> -   Библиотека типов с таким именем в данном местоположении не существует.<br />-   Библиотека типов существует, но ее версия старше передаваемой сборки.<br /><br /> Если версия библиотеки типов более новая, чем версия для передаваемой сборки, то новая библиотека не будет создана, хотя сборка будет зарегистрирована.<br /><br /> Если этот параметр указан, число его элементов должно совпадать с числом элементов для параметра `Assemblies`, иначе произойдет ошибка выполнения задачи.  Если входные данные не указаны, то для сборки в задаче будет назначено имя по умолчанию, а расширение элемента будет изменено на .tlb.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `RegisterAssembly` используется для регистрации сборки, заданной в коллекции элементов `MyAssemblies`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)