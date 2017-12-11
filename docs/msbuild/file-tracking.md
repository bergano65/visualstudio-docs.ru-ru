---
title: "Отслеживание файлов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a43c651b6f39e53b77eabe261c67ad7ca0fdcf78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="file-tracking"></a>Отслеживание файлов
Журналы отслеживания файлов отправляют в файловую систему Windows вызов процесса и его дочерних процессов. Вызывая указанные ниже функции, программы управляют включением и отключением ведения журнала, а также задают нужный файл журнала.  
  
## <a name="in-this-section"></a>Содержание  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Останавливает отслеживание в текущем контексте.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Возобновляет отслеживания после вызова [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Задает количество потоков, используемых для отслеживания.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Запускает новый контекст отслеживания.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Запускает новый контекст отслеживания с указанным корнем.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Завершает отслеживание и освобождает использованные ресурсы.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Временно приостанавливает отслеживание.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Записывает журналы отслеживания для всех контекстов.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Записывает журнал отслеживания для текущего контекста.