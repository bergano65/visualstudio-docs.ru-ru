---
title: Отслеживание файлов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156460"
---
# <a name="file-tracking"></a>Отслеживание файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Журналы отслеживания файлов отправляют в файловую систему Windows вызов процесса и его дочерних процессов. Вызывая указанные ниже функции, программы управляют включением и отключением ведения журнала, а также задают нужный файл журнала.  
  
## <a name="in-this-section"></a>В этом разделе  
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
