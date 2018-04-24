---
title: Элемент UsingTask (MSBuild) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f95e09639e9236b64f9c18c9bd90e6850ee13d86
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="usingtask-element-msbuild"></a>Элемент UsingTask (MSBuild)
Сопоставляет задачу, на которую указана ссылка в элементе [Задача](../msbuild/task-element-msbuild.md), со сборкой, содержащей реализацию этой задачи.  

 \<Project>  
 \<UsingTask>  

## <a name="syntax"></a>Синтаксис  

```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание:|  
|---------------|-----------------|  
|`AssemblyName`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Имя загружаемой сборки. Атрибут `AssemblyName` принимает сборки со строгими именами, хотя строгое именование не является обязательным. Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.Load%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyFile`.|  
|`AssemblyFile`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Путь к файлу сборки. Этот атрибут принимает полные пути или относительного пути. Относительные пути задаются относительно каталога файла проекта или файла целей построения, где объявлен элемент `UsingTask`. Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.LoadFrom%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyName`.|  
|`TaskFactory`|Необязательный атрибут.<br /><br /> Указывает класс в сборке, которая отвечает за создание экземпляров указанного имени `Task`.  Пользователь также может указать `TaskBody` в качестве дочернего элемента, который фабрика задач получает и использует для создания задачи. Содержимое `TaskBody` зависит от фабрики задач.|  
|`TaskName`|Обязательный атрибут.<br /><br /> Имя задачи для ссылки из сборки. Если возможны неоднозначности, этот атрибут должен всегда указывать полные пространства имен. При наличии неоднозначностей MSBuild выбирает произвольное соответствие, которое может привести к непредвиденным результатам.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Набор параметров, которые отображаются в задаче, создаваемой с помощью указанного `TaskFactory`.|  
|[Задача](../msbuild/task-element-msbuild.md)|Данные, передаваемые в `TaskFactory` для создания экземпляра задачи.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="remarks"></a>Примечания  
 На переменные среды, свойства командной строки и свойства уровня проекта можно ссылаться в любом месте элемента `UsingTask`, если он отображается в файле проекта либо явно, либо через импортированный файл проекта. Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  

> [!NOTE]
>  Свойства уровня проекта не имеют смысла, если элемент `UsingTask` получен из одного из файлов TASKS, зарегистрированных глобально в модуле MSBuild. Свойства уровня проекта не являются глобальными по отношению к MSBuild.  

 В MSBuild 4.0 задачи можно загрузить из файлов OVERRIDETASK.  

## <a name="example"></a>Пример  
 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyName`.  

```xml  
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

## <a name="example"></a>Пример  
 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyFile`.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
