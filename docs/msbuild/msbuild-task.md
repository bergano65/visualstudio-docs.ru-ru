---
title: "Задача MSBuild | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild - задача [MSBuild]"
  - "MSBuild, задача MSBuild"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Построение проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] из другого проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Параметры  
 В следующей таблице описаны параметры задачи `MSBuild`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`BuildInParallel`|Необязательный параметр типа `Boolean`.<br /><br /> Если присвоено значение `true`, построение проектов, указанных в параметре `Projects`, выполняется параллельно \(если это возможно\).  По умолчанию используется значение `false`.|  
|`Projects`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задание файлов проекта для построения.|  
|`Properties`|Необязательный параметр типа `String`.<br /><br /> Список пар имен "имя\-значение" свойства, разделенных точкой с запятой, которые применяются к дочернему проекту в качестве глобальных свойств.  Если этот параметр задан, от является функционально равнозначным заданию свойств с переключателем **\/property** при построении с помощью [MSBuild.exe](../msbuild/msbuild-command-line-reference.md).  Например:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> При передаче свойств проекту через параметр `Properties` [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] создает новый экземпляр проекта, даже если файл проекта уже загружен.  После создания нового экземпляра проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] обрабатывает его как другой проект с другими глобальными свойствами, построение которого может выполняться параллельно с другими экземплярами проекта.  Например, построение конфигурации выпуска может выполняться одновременно с построением конфигурации отладки.|  
|`RebaseOutputs`|Необязательный параметр типа `Boolean`.<br /><br /> Если присвоено значение `true`, относительные пути целевых выходных элементов из созданных проектов изменяются таким образом, чтобы они соответствовали вызывающему проекту.  По умолчанию используется значение `false`.|  
|`RemoveProperties`|Необязательный параметр типа `String`.<br /><br /> Задает набор глобальных свойств, которые необходимо удалить.|  
|`RunEachTargetSeparately`|Необязательный параметр типа `Boolean`.<br /><br /> Если присвоено значение `true`, задача [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] вызывает целевые объекты из списка, переданного в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], по одному, а не все одновременно.  Присвоение этому параметру значения `true` обеспечивает, что последующие целевые объекты вызываются даже при сбое ранее вызванных целевых объектов.  В противном случае ошибка построения препятствует вызову всех последующих целевых объектов.  По умолчанию используется значение `false`.|  
|`SkipNonexistentProjects`|Необязательный параметр типа `Boolean`.<br /><br /> Если значение `true`, отсутствующие на диске файлы проекта будут пропущены.  В противном случае такие проекты приведет к ошибке.|  
|`StopOnFirstFailure`|Необязательный параметр типа `Boolean`.<br /><br /> Если значение — `true`, то при ошибке построения одного из проектов построение других проектов не выполняется.  В настоящее время при параллельном построении \(с несколькими процессорами\) это не поддерживается.|  
|`TargetAndPropertyListSeparators`|Необязательный параметр типа `String[]`.<br /><br /> Определяет список целевых объектов и свойств как `Project`.  Разделители будут корректно учтены до обработки.  например.. избеганное %3B \("; "\), как если бы оно было отменить избеганное "; ".|  
|`TargetOutputs`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`, предназначенный только для чтения.<br /><br /> Возвращает выходные данные целевых объектов построения из всех файлов проекта.  Возвращаются только указанные выходные данные из целевых объектов, а не все выходные данные, которые могут существовать в целевых объектах или от которых эти объекты зависят.<br /><br /> Параметр `TargetOutputs` также содержит следующие метаданные:<br /><br /> -   `MSBuildSourceProjectFile`: файл проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], содержащий целевой объект, который задает выходные данные.<br />-   `MSBuildSourceTargetName`: целевой объект, который задает выходные данные. **Note:**  Если необходимо определить выходные данные раздельно из каждого файла проекта или целевого объекта, запустите задачу `MSBuild` отдельно для каждого файла проекта или целевого объекта.  Если задача `MSBuild` запускается только один раз для построения всех файлов проекта, выходные данные всех целевых объектов собираются в один массив.|  
|`Targets`|Необязательный параметр типа `String`.<br /><br /> Указание одного или нескольких целевых объектов для построения в файлах проекта.  Для разделения списка имен целевых объектов используется точка с запятой.  Если целевые объекты в задаче `MSBuild` не заданы, в создаваемых файлах проекта указываются целевые объекты по умолчанию. **Note:**  Целевые объекты должны входить во все файлы проекта.  В противном случае возникает сообщение об ошибке.|  
|`ToolsVersion`|Необязательный параметр типа `String`.<br /><br /> Указывает `ToolsVersion` для использования при построении проектов, переданных этой задаче.<br /><br /> Включает задачу [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для построения проекта, предназначенного для версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], отличной от указанной в данном проекте.  Допустимые значения: `2.0`, `3.0` и `3.5`.  Значение по умолчанию — `3.5`.|  
|`UnloadProjectsOnCompletion`|Необязательный параметр типа `Boolean`.<br /><br /> Если значение `true`, после завершения операции проект будет выгружен.|  
|`UseResultsCache`|Необязательный параметр типа `Boolean`.<br /><br /> Если `true`, то кэшированный результат возвращается, если существует.  Если theMSBuild задача выполняется, ее результат будет кэширован в области \(ProjectFileName, GlobalProperties\) \[TargetNames\]<br /><br /> в виде списка элементов построения|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
 В отличие от использования [Задача Exec](../msbuild/exec-task.md) для запуска MSBuild.exe эта задача использует тот же процесс [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для построения дочерних проектов.  Список построенных целевых объектов, которые могут быть пропущены, используется совместно родительскими и дочерними сборками.  Эта задача выполняется быстрее, так как не создается новый процесс [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Эта задача может обрабатывать не только файлы проекта, но и файлы решений.  
  
 Любая конфигурация, которая требуется [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для одновременного построения проектов, даже если конфигурация включает в себя удаленную инфраструктуру \(например порты, протоколы, тайм\-ауты, повторные попытки и так далее\), должна быть сделана настраиваемой с помощью файла конфигурации.  Желательно наличие возможности задания элементов конфигурации как параметров задачи в задаче `MSBuild`.  
  
 Начиная с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] версии 3.5, проекты решений получают значение TargetOutputs из всех создаваемых подпроектов.  
  
## Передача свойств в проекты  
 В версиях [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], предшествующих [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, передача различных наборов свойств в разные проекты, указанные в элементе [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], была затруднена.  При использовании атрибута Properties [MSBuild Task](../msbuild/msbuild-task.md) его настройки применялись ко всем создаваемым проектам, если только задача [MSBuild Task](../msbuild/msbuild-task.md) не выполнялась в пакетном режиме, а для каждого проекта в списке этого элемента не были заданы различные свойства.  
  
 Однако в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 представлены два новых зарезервированных элемента метаданных — Properties и AdditionalProperties, которые предоставляют гибкий способ передачи различных свойств в разные создаваемые проекты с помощью [MSBuild Task](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Эти новые элементы метаданных применяются только к элементам, переданным в атрибут Projects задачи [MSBuild Task](../msbuild/msbuild-task.md).  
  
## Преимущества многопроцессорного построения  
 Одно из главных преимуществ использования новых метаданных проявляется при параллельном построении проектов на многопроцессорной системе.  Эти метаданные позволяют консолидировать все проекты в один вызов [MSBuild Task](../msbuild/msbuild-task.md) без выполнения задач пакетной или условной обработки [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  При вызове одной задачи [MSBuild Task](../msbuild/msbuild-task.md) выполняется параллельное построение всех проектов, перечисленных в атрибуте Projects.  \(Однако это будет выполнено только в том случае, если в [MSBuild Task](../msbuild/msbuild-task.md) присутствует атрибут `BuildInParallel=true`.\) Для получения дополнительной информации см. [Параллельное построение нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## Метаданные Properties  
 Обычный сценарий заключается в построении нескольких файлов решений с помощью [MSBuild Task](../msbuild/msbuild-task.md), но с использованием различных конфигураций сборки.  Можно построить решение a1 с помощью конфигурации отладки, а решение a2 — с помощью конфигурации выпуска.  В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 этот файл проекта принял бы следующий вид:  
  
> [!NOTE]
>  В приведенном ниже примере "…" обозначает дополнительные файлы решений.  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 С помощью метаданных Properties можно упростить этот код, используя одну задачу [MSBuild Task](../msbuild/msbuild-task.md), как показано ниже:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- или \-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## Метаданные AdditionalProperties  
 Рассмотрим следующий сценарий, в котором построение двух файлов решений выполняется с помощью [MSBuild Task](../msbuild/msbuild-task.md); для обоих файлов используется конфигурация выпуска, но для одного используется архитектура x86, а для другого — архитектура ia64.  В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 потребовалось бы создать несколько экземпляров [MSBuild Task](../msbuild/msbuild-task.md): один для построения проекта с помощью конфигурации выпуска с архитектурой x86, а другой для построения проекта с помощью конфигурации выпуска с архитектурой ia64.  Файл проекта принял бы следующий вид:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 С помощью метаданных AdditionalProperties можно упростить этот код, используя одну задачу [MSBuild Task](../msbuild/msbuild-task.md), как показано ниже:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## Пример  
 В следующем примере задача `MSBuild` используется для построения проектов, определяемых коллекцией элементов `ProjectReferences`.  Полученные выходные данные целевых объектов сохраняются в коллекции элементов `AssembliesBuiltByChildProjects`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)