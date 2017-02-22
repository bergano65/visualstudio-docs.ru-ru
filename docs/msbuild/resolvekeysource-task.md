---
title: "Задача ResolveKeySource | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveKeySource - задача"
  - "ResolveKeySource - задача [MSBuild]"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача ResolveKeySource
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет источник ключа строгого имени.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `ResolveKeySource`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AutoClosePasswordPromptShow`|Необязательный параметр типа `Int32`.<br /><br /> Возвращает или задает промежуток времени в секундах, в течение которого отображается сообщение с отсчетом времени.|  
|`AutoClosePasswordPromptTimeout`|Необязательный параметр типа `Int32`.<br /><br /> Возвращает или задает время ожидания закрытия диалогового окна запроса пароля в секундах.|  
|`CertificateFile`|Необязательный параметр типа `String`.<br /><br /> Возвращает или задает путь к файлу сертификата.|  
|`CertificateThumbprint`|Необязательный параметр типа `String`.<br /><br /> Возвращает или задает отпечаток сертификата.|  
|`KeyFile`|Необязательный параметр типа `String`.<br /><br /> Возвращает или задает путь к файлу ключа.|  
|`ResolvedKeyContainer`|Необязательный выходной параметр типа `String`.<br /><br /> Возвращает или задает контейнер разрешенного ключа.|  
|`ResolvedKeyFile`|Необязательный выходной параметр типа `String`.<br /><br /> Возвращает или задает файл разрешенного ключа.|  
|`ResolvedThumbprint`|Необязательный выходной параметр типа `String`.<br /><br /> Возвращает или задает отпечаток разрешенного сертификата.|  
|`ShowImportDialogDespitePreviousFailures`|Необязательный параметр типа `Boolean`.<br /><br /> Если `true`, отображает диалоговое окно импорта, несмотря на предыдущие сбои.|  
|`SuppressAutoClosePasswordPrompt`|Необязательный параметр типа `Boolean`.<br /><br /> Возвращает или задает логическое значение, которое указывает, действительно ли диалоговое окно запроса пароля не должно закрываться автоматически.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)