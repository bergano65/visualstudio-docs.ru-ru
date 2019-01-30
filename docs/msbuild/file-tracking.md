---
title: Отслеживание файлов | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 878d4d7e56c51d8a41a0e3cf3e78d6c83ed5d0b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027676"
---
# <a name="file-tracking"></a>Отслеживание файлов
Журналы отслеживания файлов отправляют в файловую систему Windows вызов процесса и его дочерних процессов. Вызывая указанные ниже функции, программы управляют включением и отключением ведения журнала, а также задают нужный файл журнала.  
  
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