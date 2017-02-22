---
title: "Отслеживание файлов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, отслеживание файлов"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Отслеживание файлов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Функция отслеживания файлов записывает для процессов и подчиненных процессов вызовы, отправленные в файловую систему Windows.  Вызовы представленных ниже функций позволяют программам управлять включением функции отслеживания и указывать используемый файл журнала.  
  
## В этом подразделе  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Прекращение отслеживания текущего контекста.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Продолжение отслеживания после вызова [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Установка количества потоков, используемых для отслеживания.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Начало нового контекста отслеживания.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Начало нового контекста отслеживания с указанным корневым каталогом.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Завершение отслеживания и освобождение использованных ресурсов.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Временная приостановка отслеживания.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Запись журналов отслеживания для всех контекстов.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Запись журнала отслеживания для текущего контекста.