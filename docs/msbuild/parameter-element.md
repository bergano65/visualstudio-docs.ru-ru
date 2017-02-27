---
title: "Элемент Parameter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<Parameter> - элемент [MSBuild]"
  - "Parameter - элемент [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Элемент Parameter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит сведения о определенном параметре для задачи, которая формируется в `UsingTask` `TaskFactory`.  Имя элемента является именем параметра.  Для получения дополнительной информации смотрите [Элемент UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Синтаксис  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`ParameterType`|Необязательный атрибут.<br /><br /> Тип параметра .NET, например «System.String».|  
|`Output`|Необязательный атрибут логического типа.<br /><br /> Если `true`, параметр является выходным для задачи.  Значение по умолчанию — `false`.|  
|`Required`|Необязательный атрибут логического типа.<br /><br /> Если `true`, параметр является обязательным для задачи.  Значение по умолчанию — `false`.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Содержит необязательный список параметров, которые будут присутствовать у задачи, созданной `UsingTask` `TaskFactory`.|  
  
## Пример  
 В приведенном ниже примере показано использование элемента `Parameter`.  
  
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