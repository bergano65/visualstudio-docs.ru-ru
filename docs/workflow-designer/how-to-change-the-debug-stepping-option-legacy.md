---
title: 'Конструктор рабочих процессов - как: изменить вариант пошаговой отладки (для прежних версий)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971987"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Как изменить вариант пошаговой отладки (для прежних версий)

В этом разделе описывается изменение вариант для приложений Windows Workflow Foundation (WF) в конструкторе рабочих процессов прежних версий Windows, имеющих параллельные действия пошаговой отладки. Используйте конструктор рабочих процессов прежних версий, для целевой платформы .NET Framework 3.5 или WinFX.

При отладке действий прежних версий, которые выполняются одновременно, таких как **ParallelActivity** или **ConditionedActivityGroup**, можно использовать один из двух вариантов для пошаговой проверки кода.

Выполните следующие действия, чтобы изменить вариант пошаговой отладки в проекте рабочего процесса прежних версий.

## <a name="procedures"></a>Процедуры

### <a name="to-change-the-debug-stepping-option"></a>Изменение варианта пошаговой отладки

1.  Запустите Visual Studio.

2.  Откройте существующий проект рабочего процесса прежних версий или создайте новый проект, в котором используются параллельные действия и который нацелен WinFX или .NET Framework версии 3.5.

3.  На **рабочего процесса** меню в конструкторе рабочих процессов прежних версий, укажите **отладки**, а затем **варианты пошаговой отладки**.

4.  Выберите либо **экземпляр** или **ветви**.

## <a name="see-also"></a>См. также

- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)
- [Варианты пошаговой отладки (для прежних версий)](../workflow-designer/debug-stepping-options-legacy.md)