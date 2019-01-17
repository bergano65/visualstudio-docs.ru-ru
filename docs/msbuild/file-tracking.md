---
title: Отслеживание файлов | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b99934091ed617aa6c6bf2163391aa0d79c5414
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861670"
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