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
ms.openlocfilehash: 7ee4620e845205a936bbdf48a9872c4dec3305ea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596038"
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
