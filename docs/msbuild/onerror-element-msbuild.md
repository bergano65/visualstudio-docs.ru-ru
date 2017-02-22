---
title: "Элемент OnError (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<OnError> - элемент [MSBuild]"
  - "OnError - элемент [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Элемент OnError (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Выполнение одного или нескольких целевых объектов, если атрибуту `ContinueOnError` присвоено значение `false` для задачи, вызвавшей сбой.  
  
## Синтаксис  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Обязательный атрибут.<br /><br /> Целевые объекты, выполняемые в случае сбоя задачи.  Несколько целевых объектов отделяются друг от друга точкой с запятой.  При наличии нескольких целевых объектов они выполняются в том порядке, в котором были указаны.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Целевой объект](../msbuild/target-element-msbuild.md)|Элемент\-контейнер для задач [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Заметки  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполняет элемент `OnError` если одна из задач элемента `Target` завершается неудачей с атрибутом `ContinueOnError` к `ErrorAndStop` \(или `false`\).  При сбое задачи выполняются целевые объекты, заданные в атрибуте `ExecuteTargets`.  Если в целевом объекте более одного элемента `OnError`, то при сбое задачи элементы `OnError` выполняются по очереди.  
  
 Дополнительные сведения об атрибуте `ContinueOnError` см. в разделе [Элемент Task \(MSBuild\)](../msbuild/task-element-msbuild.md).  Дополнительные сведения о целевых объектах см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md).  
  
## Пример  
 В следующем примере кода выполняются задачи `TaskOne` и `TaskTwo`.  Если происходит сбой `TaskOne`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] проверяет значение элемента `OnError` и выполняет целевой объект `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)