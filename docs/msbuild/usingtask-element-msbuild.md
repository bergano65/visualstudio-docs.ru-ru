---
title: "Элемент UsingTask (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<UsingTask> - элемент [MSBuild]"
  - "UsingTask - элемент [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Элемент UsingTask (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сопоставляет задачу, на которую имеется ссылка в элементе [Задача](../msbuild/task-element-msbuild.md), со сборкой, содержащей реализацию этой задачи.  
  
## Синтаксис  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`AssemblyName`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Имя загружаемой сборки.  Атрибут `AssemblyName` принимает сборки со строгими именами, хотя строгое именование не является обязательным.  Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.Load%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyFile`.|  
|`AssemblyFile`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Путь к файлу сборки.  Этот атрибут принимает полные пути или относительного пути.  Относительные пути задаются относительно каталога файла проекта или файла целей построения, где объявлен элемент `UsingTask`.  Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.LoadFrom%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyName`.|  
|`TaskFactory`|Необязательный атрибут.<br /><br /> Указывает класс в сборке, которая отвечает за создание экземпляров указанного имени `Task`.  Пользователь также может указать `TaskBody` в качестве дочернего элемента, который фабрика задач получает и использует для создания задачи.  Содержимое `TaskBody` зависит от фабрики задач.|  
|`TaskName`|Обязательный атрибут.<br /><br /> Имя задачи для ссылки из сборки.  Если возможны неоднозначности, этот атрибут должен всегда указывать полные пространства имен.  При наличии неоднозначностей MSBuild выбирает произвольное соответствие, которое может привести к непредвиденным результатам.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Набор параметров, которые отображаются в задаче, создаваемой с помощью указанного `TaskFactory`.|  
|[Задача](../msbuild/task-element-msbuild.md)|Данные, передаваемые в `TaskFactory` для создания экземпляра задачи.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Project](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Заметки  
 На переменные среды, свойства командной строки и свойства уровня проекта можно ссылаться в любом месте элемента `UsingTask`, если он отображается в файле проекта либо явно, либо через импортированный файл проекта.  Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Свойства уровня проекта не имеют смысла, если элемент `UsingTask` получен из одного из файлов TASKS, зарегистрированных глобально в модуле MSBuild.  Свойства уровня проекта не являются глобальными по отношению к MSBuild.  
  
 В MSBuild 4.0 задачи можно загрузить из файлов OVERRIDETASK.  
  
## Пример  
 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyName`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Пример  
 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyFile`.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)