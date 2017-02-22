---
title: "Элемент TaskBody (MSBuild) | Microsoft Docs"
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
  - "<TaskBody> - элемент [MSBuild]"
  - "TaskBody - элемент [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Элемент TaskBody (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит данные, которые передаются `UsingTask` `TaskFactory`. Для получения дополнительной информации см. [Элемент UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Синтаксис  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Evaluate`|Необязательный атрибут логического типа.<br /><br /> Если `true`, MSBuild оценивает любые внутренние элементы и расширяет элементы и свойства перед передачей информации в `TaskFactory`, при создании экземпляра задачи.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Данные|Текст между тегами`TaskBody` отправляется буквально в `TaskFactory`.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Позволяет регистрировать задачи в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  В проекте может быть любое число элементов `UsingTask`, включая ноль.|  
  
## Пример  
 В следующем примере показано, как использовать элемент `TaskBody` с атрибутом `Evaluate`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)