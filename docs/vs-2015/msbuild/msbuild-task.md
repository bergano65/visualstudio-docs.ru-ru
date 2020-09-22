---
title: Задача MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2349c21d55c20bcb3bcd50ab96f383a9afcc00b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843176"
---
# <a name="msbuild-task"></a>Задача MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выполняет сборку проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] на основе другого проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `MSBuild` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`BuildInParallel`|Необязательный параметр `Boolean`.<br /><br /> Если его значение `true`, то сборка проектов, указанных в параметре `Projects`, выполняется параллельно, по возможности. Значение по умолчанию — `false`.|  
|`Projects`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Он определяет файлы проекта, необходимые для сборки.|  
|`Properties`|Необязательный параметр `String`.<br /><br /> Список разделенных точкой с запятой пар имя-значение для применения в качестве глобальных свойств к дочернему проекту. При указании этого параметра он функционально эквивалентен настройке свойств с параметром **/Property** при построении с [MSBuild.exe](../msbuild/msbuild-command-line-reference.md). Пример:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> При передаче проекту свойств с помощью параметра `Properties`[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] создает новый экземпляр проекта даже в том случае, если файл проекта уже загружен. При создании нового экземпляра проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] обрабатывает его как другой проект с другими глобальными свойствами, сборка которого может выполняться параллельно с другими экземплярами проекта. Например, сборка конфигурации выпуска может выполняться в одно время со сборкой конфигурации отладки.|  
|`RebaseOutputs`|Необязательный параметр `Boolean`.<br /><br /> Если его значение `true`, то относительные пути целевых выходных элементов из созданных проектов корректируются таким образом, чтобы соответствовать вызывающему проекту. Значение по умолчанию — `false`.|  
|`RemoveProperties`|Необязательный параметр `String`.<br /><br /> Задает набор глобальных свойств для удаления.|  
|`RunEachTargetSeparately`|Необязательный параметр `Boolean`.<br /><br /> Если его значение `true`, то задача [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] вызывает каждый целевой объект из списка, переданного в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], по одному, а не все одновременно. Задание для этого параметра значения `true` гарантирует вызов последующих целевых объектов даже в случае сбоя ранее вызванных объектов. В противном случае из-за сбоя во время сборки какого-то одного объекта вызов всех последующих целевых объектов прекратится. Значение по умолчанию — `false`.|  
|`SkipNonexistentProjects`|Необязательный параметр `Boolean`.<br /><br /> Если его значение `true`, то файлы проекта, не существующие на диске, будут пропущены. В противном случае такие проекты приведут к ошибке.|  
|`StopOnFirstFailure`|Необязательный параметр `Boolean`.<br /><br /> Если его значение `true`, то в случае, если происходит сбой во время сборки одного из проектов, сборка остальных проектов не будет выполнена. В настоящее время не поддерживается при параллельной сборке (с несколькими процессорами).|  
|`TargetAndPropertyListSeparators`|Необязательный параметр `String[]`.<br /><br /> Определяет список целевых объектов и свойств в качестве метаданных элемента `Project`). Разделители будут восстановлены перед обработкой. Например, выражение %3B (экранированный знак ";") будет рассматриваться как восстановленный знак ";".|  
|`TargetOutputs`|Необязательный параметр вывода <xref:Microsoft.Build.Framework.ITaskItem>`[]`, доступный только для чтения.<br /><br /> Возвращает выходные данные построенных целевых объектов из всех файлов проекта. Возвращаются только выходные данные целевых объектов, которые были заданы, а не выходные данные, которые могут существовать в целевых объектах, от которых зависят первые.<br /><br /> Параметр `TargetOutputs` также содержит следующие метаданные:<br /><br /> -   `MSBuildSourceProjectFile`. Файл проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], который содержит целевой объект, определяющий выходные данные.<br />-   `MSBuildSourceTargetName`: Целевой объект, определяющий выходные данные. **Примечание.**  Если нужно определить выходные данные из каждого файла проекта или целевого объекта отдельно, запустите задачу `MSBuild` отдельно для каждого файла проекта или целевого объекта. Если вы запустите задачу `MSBuild` один раз для сборки всех файлов проекта, выходные данные всех целевых объектов будут собраны в один массив.|  
|`Targets`|Необязательный параметр `String`.<br /><br /> Определяет целевой объект (или объекты) для сборки в файлах проекта. Используйте точку с запятой для разделения списка имен целевых объектов. Если целевые объекты в задаче `MSBuild` не заданы, будет выполнена сборка целевых объектов по умолчанию, заданных в файлах проекта. **Примечание.**  Целевые объекты должны быть указаны во всех файлах проекта. Если это не так, при сборке возникает ошибка.|  
|`ToolsVersion`|Необязательный параметр `String`.<br /><br /> Определяет `ToolsVersion`, используемую при сборке проектов, для передачи в эту задачу.<br /><br /> Позволяет задаче [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] выполнить сборку проекта, предназначенного для версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], отличающейся от той, которая указана в проекте. Допустимые значения: `2.0`, `3.0` и `3.5`. Значение по умолчанию — `3.5`.|  
|`UnloadProjectsOnCompletion`|Необязательный параметр `Boolean`.<br /><br /> Если это значение `true`, проект будет выгружен после завершения операции.|  
|`UseResultsCache`|Необязательный параметр `Boolean`.<br /><br /> Если это значение `true`, будет возвращен кэшированный результат, если он имеется. При запуске задачи theMSBuild ее результат будет кэшироваться в области (ProjectFileName, GlobalProperties)[TargetNames]<br /><br /> как список элементов сборки|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
 В отличие от использования [задачи Exec](../msbuild/exec-task.md) для запуска MSBuild.exe, эта задача использует тот же процесс [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] для создания дочерних проектов. Список уже собранных целевых объектов, которые могут быть пропущены, доступен как родительским, так и дочерним сборкам. Эта задача выполняется быстрее, так как при этом не создаются новые процессы [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Эта задача может обрабатывать не только файлы проекта, но также файлы решения.  
  
 Все конфигурации, которые требует [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] для того, чтобы сборка проектов выполнялась в одно время, даже если конфигурация включает в себя удаленные инфраструктуры (например, порты, протоколы, тайм-ауты, повторные попытки и т. д.), должны быть доступны для настройки с помощью файла конфигурации. Рекомендуется для элементов конфигурации предусмотреть возможность указания их в виде параметров для задачи `MSBuild`.  
  
 Начиная с версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, проекты решения извлекают конечные выходные данные из всех подпроектов, которые он создает.  
  
## <a name="passing-properties-to-projects"></a>Передача свойств в проекты  
 В версиях [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] более ранних, чем [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, передачу разных наборов свойств в разные проекты, перечисленные в элементе [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], было непросто осуществить. Если вы использовали атрибут Properties [задачи MSBuild](../msbuild/msbuild-task.md), то его настройка была применена ко всем сборкам проектов, если не выполнялась пакетирование [задачи MSBuild](../msbuild/msbuild-task.md) и условно не предоставлены различные свойства для каждого проекта в списке элементов.  
  
 В версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 зарезервированы два новых элемента метаданных, Properties и AdditionalProperties, позволяющие легко передавать разные свойства в разные проекты, сборка которых выполнена с помощью [задачи MSBuild](../msbuild/msbuild-task.md).  
  
> [!NOTE]
> Эти новые элементы метаданных применимы только к элементам, передаваемым в атрибуте Projects [задачи MSBuild](../msbuild/msbuild-task.md).  
  
## <a name="multi-processor-build-benefits"></a>Преимущества сборок в системах с несколькими процессорами  
 Одно из основных преимуществ использования новых метаданных проявляется при выполнении сборок проектов в параллельном режиме в системах с несколькими процессорами. Метаданные позволяют объединить все проекты в один вызов [задачи MSBuild](../msbuild/msbuild-task.md) вместо того, чтобы выполнять пакетную обработку или задачи [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] с разными условиями. И при вызове только одной [задачи MSBuild](../msbuild/msbuild-task.md)все проекты, перечисленные в атрибуте Projects, будут создаваться параллельно. (Однако, только если `BuildInParallel=true` атрибут имеется в [задаче MSBuild](../msbuild/msbuild-task.md).) Дополнительные сведения см. [в разделе параллельное создание нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Метаданные Properties  
 Распространенный сценарий состоит в том, что при построении нескольких файлов решения с помощью [задачи MSBuild](../msbuild/msbuild-task.md)используются разные конфигурации сборки. Например, вам нужно выполнить сборку решения a1 с помощью конфигурации отладки, а решения a2 — с помощью конфигурации выпуска. В версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 такой файл проекта выглядел следующим образом:  
  
> [!NOTE]
> В следующем примере знаком "..." обозначены дополнительные файлы решения.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Однако с помощью метаданных свойств можно упростить это, чтобы использовать одну [задачу MSBuild](../msbuild/msbuild-task.md), как показано ниже:  
  
### <a name="aproj"></a>a.proj  
  
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
  
 \- или -  
  
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
  
## <a name="additionalproperties-metadata"></a>Метаданные AdditionalProperties  
 Рассмотрим следующую ситуацию, когда вы создаете два файла решения с помощью [задачи MSBuild](../msbuild/msbuild-task.md), используя конфигурацию выпуска, но один использует архитектуру x86, а другой — архитектуру IA64. В версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 вам потребовалось бы создать несколько экземпляров [задачи MSBuild](../msbuild/msbuild-task.md). Один — для сборки проекта с помощью конфигурации выпуска с архитектурой x86, другой — с помощью конфигурации выпуска с архитектурой ia64. Файл проекта выглядел бы следующим образом:  
  
### <a name="aproj"></a>a.proj  
  
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
  
 С помощью метаданных AdditionalProperties можно упростить это для использования одной [задачи MSBuild](../msbuild/msbuild-task.md) с помощью следующих средств:  
  
### <a name="aproj"></a>a.proj  
  
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
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `MSBuild` для сборки проектов, определенных коллекцией элементов `ProjectReferences`. Полученные конечные выходные данные хранятся в коллекции элементов `AssembliesBuiltByChildProjects`.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
