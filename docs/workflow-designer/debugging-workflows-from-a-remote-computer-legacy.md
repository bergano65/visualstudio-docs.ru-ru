---
title: "Отладка рабочих процессов с удаленного компьютера (для прежних версий) | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be8c1f6a049224cc5b79a82dc6bc100840c72fd0
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Отладка рабочих процессов с удаленного компьютера (для прежних версий)
В этом разделе описывается отладка удаленных прежних версий [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] приложений, созданных в конструкторе рабочих процессов прежних версий Windows. Используйте средство [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 При установке [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], один из вариантов установки компонентов является установка [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] отладчика для [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. При этом устанавливаются компоненты удаленной отладки. Эти компоненты удаленной отладки должны быть установлены на компьютер, который будет использоваться в целях удаленной отладки рабочих процессов.

 Кроме того, сборка, содержащая определение рабочего процесса более ранней версии, отладка которого выполняется на удаленном компьютере, должна быть установлена в глобальный кэш сборок (GAC) на локальном компьютере, на котором выполняется отладка. Например, если рабочий процесс более ранней версии выполняется на удаленном компьютере А и его отладка выполняется с локального компьютера В, определение рабочего процесса должно находиться в GAC компьютера В. Это позволяет конструктору выполнить десериализацию и показать на компьютере В разметку рабочего процесса, который выполняется удаленно на компьютере А. Дополнительные сведения о глобальном кэше сборок (GAC) см. в библиотеке MSDN.

 Функции удаленной отладки [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] такие же, как у удаленной отладки других компонентов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] удаленную отладку в библиотеке MSDN.

## <a name="see-also"></a>См. также

- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)