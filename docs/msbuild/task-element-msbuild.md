---
title: "Элемент Task (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Task> - элемент [MSBuild]"
  - "Task - элемент [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Элемент Task (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает и запускает экземпляр задачи [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Имя элемента определяется именем создаваемой задачи.  
  
## Синтаксис  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Condition`|Необязательный атрибут.  Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Необязательный атрибут.  Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**.  При сбое задачи, последующие задачи в элементе [целевой объект](../msbuild/target-element-msbuild.md) и построении продолжают выполняться, и все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**.  При сбое задачи, последующие задачи в элементе `Target` и построении продолжают выполняться, и все ошибки из задачи следует обрабатывать как ошибки.<br />-   **ErrorAndStop** или **false** \(по умолчанию\).  При сбое задачи, не исполнены остальные задачи в элементе `Target` и построении и считается, что не удалось весь элемент `Target` и построение.<br /><br /> Версии платформы .NET Framework до 4,5 поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в разделе [Практическое руководство. Игнорирование ошибок в задачах](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md).|  
|`Parameter`|Обязательный атрибут в случае, если класс содержит одно или несколько свойств с атрибутом `[Required]`.<br /><br /> Определяемый пользователем параметр задачи, значением которого является значение параметра.  Элемент `Task` может содержать любое число параметров, и каждый атрибут соответствует свойству .NET в классе задачи.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Output](../msbuild/output-element-msbuild.md)|Задает сохранение выходных данных задачи в файле проекта.  Задача может содержать любое число элементов `Output`, включая ноль.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Целевой объект](../msbuild/target-element-msbuild.md)|Элемент\-контейнер для задач [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Заметки  
 Элемент `Task` в файле проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] создает экземпляр задачи, устанавливает его свойства и запускает его.  Элемент `Output` сохраняет выходные параметры в свойствах или элементах, используемых в других местах файла проекта.  
  
 Если в родительском элементе `Target` задачи имеются элементы [OnError](../msbuild/onerror-element-msbuild.md), они будут обрабатываться даже в случае, если произошел сбой выполнения задачи, а `ContinueOnError` имеет значение `false`.  Дополнительные сведения о задачах см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
## Пример  
 В следующем примере кода создается экземпляр класса [Csc task](../msbuild/csc-task.md), устанавливается шесть из его свойств, после чего задача выполняется.  После выполнения значение свойства `OutputAssembly` объекта помещается в список элементов с именем `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)