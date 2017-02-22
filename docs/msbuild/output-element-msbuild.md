---
title: "Элемент Output (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> - элемент [MSBuild]"
  - "Output - элемент [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Элемент Output (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сохраняет выходные данные задачи в элементах и свойствах.  
  
## Синтаксис  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`TaskParameter`|Обязательный атрибут.<br /><br /> Название параметра выходных данных задачи.|  
|`PropertyName`|Обязательно использовать либо атрибут `PropertyName`, либо атрибут `ItemName`.<br /><br /> Свойство, получающее значение параметра выходных данных задачи.  Ссылаться на свойство можно с помощью синтаксиса `$(`*PropertyName*`)`.  Имя свойства должно быть либо новым именем свойства, либо именем, которое уже определено в проекте.<br /><br /> Этот атрибут не используется при использовании атрибута `ItemName`.|  
|`ItemName`|Обязательно использовать либо атрибут `PropertyName`, либо атрибут `ItemName`.<br /><br /> Элемент, получающий значение параметра выходных данных задачи.  Ссылаться на элемент можно с помощью синтаксиса `@(`*ItemName*`)`.  Имя элемента должно быть либо новым именем элемента, либо именем, которое уже определено в проекте.<br /><br /> Этот атрибут не используется при использовании атрибута `PropertyName`.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Задача](../msbuild/task-element-msbuild.md)|Создает и запускает экземпляр задачи [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Пример  
 В следующем примере кода показано выполнение задачи `Csc` внутри элемента `Target`.  Элементы и свойства, передаваемые в параметры задачи, объявлены вне данного примера.  Значение выходного параметра `OutputAssembly` сохраняется в элементе `FinalAssemblyName`, а значение выходного параметра `BuildSucceeded` сохраняется в свойстве `BuildWorked`.  Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)