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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2fafae7cce22cc41fdd51a4bc727ac6bfb791b9
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436628"
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
