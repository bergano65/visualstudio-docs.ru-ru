---
title: "Задача GenerateTrustInfo | Microsoft Docs"
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
  - "GenerateTrustInfo - задача [MSBuild]"
  - "MSBuild, GenerateTrustInfo - задача"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Задача GenerateTrustInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Формирование доверия к приложению на основе базового манифеста и параметров `TargetZone` и `ExcludedPermissions`.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `GenerateTrustInfo`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`ApplicationDependencies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет зависимые сборки.|  
|`BaseManifest`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает Базовый манифест, на основе которого будет сформировано доверие к приложению.|  
|`ExcludedPermissions`|Необязательный параметр типа `String`.<br /><br /> задает одно или несколько значений идентификаторов разрешений, отделенных друг от друга точкой с запятой, которые необходимо исключить из набора разрешений по умолчанию для зоны.|  
|`TargetZone`|Необязательный параметр типа `String`.<br /><br /> Определяет набор разрешений зоны по умолчанию, получаемый из политики компьютера.|  
|`TrustInfoFile`|Обязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает Файл, содержащий сведения о доверии к уровню безопасности приложения.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)