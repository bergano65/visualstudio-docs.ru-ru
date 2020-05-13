---
title: Отслеживание файлов | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634205"
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
