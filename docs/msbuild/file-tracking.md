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
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968071"
---
# <a name="file-tracking"></a>Отслеживание файлов
Журналы отслеживания файлов отправляют в файловую систему Windows вызов процесса и его дочерних процессов. Вызывая указанные ниже функции, программы управляют включением и отключением ведения журнала, а также задают нужный файл журнала.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) останавливает отслеживание в текущем контексте.

- [ResumeTracking](../msbuild/resumetracking.md) возобновляет отслеживание после вызова [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) задает количество потоков, используемых для отслеживания.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) запускает новый контекст отслеживания.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) запускает новый контекст отслеживания с указанным корнем.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) завершает отслеживание и освобождает использованные ресурсы.

- [SuspendTracking](../msbuild/suspendtracking.md) временно приостанавливает отслеживание.

- [WriteAllTLogs](../msbuild/writealltlogs.md) записывает журналы отслеживания для всех контекстов.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) записывает журнал отслеживания для текущего контекста.