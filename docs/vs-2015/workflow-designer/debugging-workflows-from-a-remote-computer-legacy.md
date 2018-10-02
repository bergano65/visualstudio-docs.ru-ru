---
title: Отладка рабочих процессов с удаленного компьютера (для прежних версий) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 458f5d2a8d2be83f465f9b96ac9ff9dd1eca2d37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562235"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Отладка рабочих процессов с удаленного компьютера (для прежних версий)
В данном разделе описывается отладка удаленных приложений [!INCLUDE[wf](../includes/wf-md.md)] более ранней версии, построенных с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии. Используйте средство [!INCLUDE[wfd2](../includes/wfd2-md.md)] более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 При установке [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], одним из вариантов установки компонентов является установка [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] отладчика для [!INCLUDE[wf](../includes/wf-md.md)]. При этом устанавливаются компоненты удаленной отладки. Эти компоненты удаленной отладки должны быть установлены на компьютер, который будет использоваться в целях удаленной отладки рабочих процессов.  
  
 Кроме того, сборка, содержащая определение рабочего процесса более ранней версии, отладка которого выполняется на удаленном компьютере, должна быть установлена в глобальный кэш сборок (GAC) на локальном компьютере, на котором выполняется отладка. Например, если рабочий процесс более ранней версии выполняется на удаленном компьютере А и его отладка выполняется с локального компьютера В, определение рабочего процесса должно находиться в GAC компьютера В. Это позволяет конструктору выполнить десериализацию и показать на компьютере В разметку рабочего процесса, который выполняется удаленно на компьютере А. Дополнительные сведения о глобальном кэше сборок (GAC) см. в библиотеке MSDN.  
  
 Функции удаленной отладки [!INCLUDE[wf2](../includes/wf2-md.md)] такие же, как у удаленной отладки других компонентов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] удаленную отладку в библиотеке MSDN.  
  
## <a name="see-also"></a>См. также  
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)