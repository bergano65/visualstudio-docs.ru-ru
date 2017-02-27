---
title: "Задача Error | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error - задача [MSBuild]"
  - "MSBuild, Error - задача"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Задача Error
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Останавливает построение и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `Error`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Code`|Необязательный параметр типа `String`.<br /><br /> Код, связанный с данной ошибкой.|  
|`File`|Необязательный параметр типа `String`.<br /><br /> Имя файла, содержащего ошибку.  Если файл не предоставлен, используется файл, содержащий задачу Error.|  
|`HelpKeyword`|Необязательный параметр типа `String`.<br /><br /> Ключевое слово справки, сопоставляемое с ошибкой.|  
|`Text`|Необязательный параметр типа `String`.<br /><br /> Текст ошибки, регистрируемый в журнале [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в случае, если результат вычисления параметра `Condition` оказывается равным `true`.|  
  
## Заметки  
 Задача `Error` позволяет передавать текст ошибок в средства ведения журнала и останавливать выполнение построения в проектах [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Если результат вычисления параметра `Condition` оказывается равным `true`, построение останавливается, и ошибка регистрируется в журнале.  Если параметр `Condition` не существует, ошибка регистрируется в журнале, и выполнение построения останавливается.  Дополнительные сведения о ведении журнала см. в разделе [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере кода проверяется, что установлены все обязательные свойства.  Если это не так, проект инициирует событие ошибки и регистрирует в журнале значение параметра `Text` задачи `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md)