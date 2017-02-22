---
title: "Задача Warning | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Warning - задача"
  - "Warning - задача [MSBuild]"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача Warning
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Запись предупреждения в журнал в процессе построения на основании вычисленного условного оператора.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `Warning`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Code`|Необязательный параметр типа `String`.<br /><br /> Код предупреждения для сопоставлением с предупреждением.|  
|`File`|Необязательный параметр типа `String`.<br /><br /> Задает соответствующий файл, если имеется.  Если файл не предоставлен, используется файл, содержащий задачу Warning.|  
|`HelpKeyword`|Необязательный параметр типа `String`.<br /><br /> Ключевое слово справки, сопоставляемое с предупреждением.|  
|`Text`|Необязательный параметр типа `String`.<br /><br /> Текст предупреждения, регистрируемый [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в случае, если параметру `Condition` присвоено значение `true`.|  
  
## Заметки  
 Задача `Warning` позволяет проектам [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполнять проверку на наличие необходимой конфигурации или свойства перед переходом к следующему этапу построения.  
  
 Если параметру `Condition` задачи `Warning` присвоено значение `true`, то значение параметра `Text` регистрируется в журнале, а процесс построения продолжается.  Если параметр `Condition` не существует, текст предупреждения регистрируется в журнале.  Дополнительные сведения о ведении журнала см. в разделе [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере кода проверяется наличие свойств, заданных из командной строки.  Если такие свойства отсутствуют, проект вызывает предупреждение и регистрирует значение параметра `Text` задачи `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## См. также  
 [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)