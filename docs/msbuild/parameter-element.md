---
title: "Элемент Parameter | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 39dd727eee6f9af2f60410c4dbfc9daa9ea805a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-element"></a>Элемент Parameter
Содержит сведения о конкретном параметре для задачи, созданной `UsingTask``TaskFactory`.  Имя элемента — это имя параметра.  Дополнительные сведения см. в статье [Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>Синтаксис  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание|  
|---------------|-----------------|  
|`ParameterType`|Необязательный атрибут.<br /><br /> Тип параметра .NET, например System.String.|  
|`Output`|Дополнительный логический атрибут.<br /><br /> Если он имеет значение `true`, этот параметр является для задачи параметром вывода. Значение по умолчанию `false`.|  
|`Required`|Дополнительный логический атрибут.<br /><br /> Если он имеет значение `true`, этот параметр является для задачи обязательным параметром. Значение по умолчанию `false`.|  

### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Содержит необязательный список параметров, которые будут присутствовать в задаче, созданной `UsingTask``TaskFactory`.|  

## <a name="example"></a>Пример  
 В следующем примере показано использование элемента `Parameter`.  

```xml  
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

## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
