---
title: Отслеживание файлов | Документы Майкрософт
description: Используйте функции отслеживания файлов MSBuild для регистрации обращений к файловой системе Windows для процесса и его дочерних процессов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877126"
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
