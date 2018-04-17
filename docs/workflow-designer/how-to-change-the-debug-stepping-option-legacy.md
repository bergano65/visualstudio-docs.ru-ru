---
title: 'Как: изменить вариант пошаговой отладки (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: aedb8e738dc2e6ca2b066dd9a2cd42e332bbd8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Как изменить вариант пошаговой отладки (для прежних версий)
В этом разделе описывается изменение варианта пошаговой отладки для [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] приложения в конструкторе рабочих процессов прежних версий Windows, параллельными действиями. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 При отладке действий прежних версий, которые выполняются одновременно, таких как **ParallelActivity** или **ConditionedActivityGroup**, можно использовать один из двух вариантов для пошаговой проверки кода.

 Выполните следующие действия, чтобы изменить вариант пошаговой отладки в проекте рабочего процесса прежних версий.

## <a name="procedures"></a>Процедуры

#### <a name="to-change-the-debug-stepping-option"></a>Изменение варианта пошаговой отладки

1.  Запустите Visual Studio.

2.  Откройте существующий проект рабочего процесса прежних версий или создайте новый проект, в котором применяются параллельные действия и который предназначен для работы с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

3.  На **рабочего процесса** меню прежних версий [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], пункты **отладки**, а затем **варианты пошаговой отладки**.

4.  Выберите либо **экземпляр** или **ветви**.

## <a name="see-also"></a>См. также

- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)
- [Варианты пошаговой отладки (для прежних версий)](../workflow-designer/debug-stepping-options-legacy.md)