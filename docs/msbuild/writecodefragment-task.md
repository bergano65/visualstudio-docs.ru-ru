---
title: "Задача WriteCodeFragment | Microsoft Docs"
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
  - "MSBuild, WriteCodeFragment - задача"
  - "WriteCodeFragment - задача [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача WriteCodeFragment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает временный файл исходного кода, созданного из указанного фрагмента кода.  Не удаляет этот файл.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `WriteCodeFragment`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AssemblyAttributes`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Описание атрибутов для записи.  Значение элемента `Include` — полное имя типа атрибута. Например, "System.AssemblyVersionAttribute".<br /><br /> Каждый фрагмент метаданных является парой имя\-значение параметра, которая должна иметь тип `String`.  Некоторые атрибуты позволяют только позиционные аргументы конструктора.  Тем не менее можно использовать такие аргументы в любом атрибуте.  Чтобы задать позиционные атрибуты конструктора, используйте имена метаданных, которые напоминают «\_Parameter1», «\_Parameter2» и так далее.<br /><br /> Индекс параметра не может быть пропущен.|  
|`Language`|Обязательный параметр типа `String`.<br /><br /> Задает язык создаваемого кода.<br /><br /> `Language` может быть любой язык, для которого доступен поставщик CodeDom, например "C\#" или "VisualBasic".  Выданный файл будет с расширением имени файла по умолчанию для соответствующего языка.|  
|`OutputDirectory`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> задает конечную папку для созданного кода \(как правило, промежуточную папку\).|  
|`OutputFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает путь к файлу, который был создан.  Если этот параметр задан с использованием имени файла, к имени файла добавляется папка назначения.  Если он задан, используя корень, папка назначения игнорируется.<br /><br /> Если этот параметр не задано, имя выходного файла равно папке назначения, произвольное имя файла и расширение по умолчанию для выбранного языка.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)