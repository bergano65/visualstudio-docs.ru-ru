---
title: "Задача CallTarget | Microsoft Docs"
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
  - "CallTarget - задача [MSBuild]"
  - "MSBuild, CallTarget - задача"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача CallTarget
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Вызов указанных целевых объектов в файле проекта.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `CallTarget`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`RunEachTargetSeparately`|Необязательный выходной параметр `Boolean`.<br /><br /> При значении `true` ядро [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] вызывается один раз для каждого целевого объекта.  При значении `false` ядро [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] вызывается один раз для построения всех целевых объектов.  Значение по умолчанию — `false`.|  
|`TargetOutputs`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Выходные файлы для всех построенных целевых объектов.|  
|`Targets`|Необязательный параметр типа `String[]`.<br /><br /> Целевой объект или объекты, которые должны быть построены.|  
|`UseResultsCache`|Необязательный параметр типа `Boolean`.<br /><br /> Если `true`, то кэшированный результат возвращается, если существует.<br /><br /> **Примечание** При запуске задачи MSBuild, ее вывод кэшируется в область \(ProjectFileName, GlobalProperties\) \[именаЦелевыхОбъектов\] как список элементов построения.|  
  
## Заметки  
 Если возникает сбой целевого объекта, заданного параметром `Targets`, и для параметра `RunEachTargetSeparately` установлено значение `true`, то задача продолжает построение остальных целевых объектов.  
  
 Если требуется построение целевых объектов по умолчанию, следует воспользоваться задачей MSBuild \(см. раздел [Задача MSBuild](../msbuild/msbuild-task.md)\) и задать для параметра `Projects` значение `$(MSBuildProjectFile)`.  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере представлен вызов целевого объекта `TargetA` из списка `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)