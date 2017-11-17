---
title: "Отладка варианты пошаговой (устаревшая версия) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbdb0d481c0740310f40f6a75d8c84db765f847d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debug-stepping-options-legacy"></a>Варианты пошаговой отладки (для прежних версий)
В этом разделе описывается отладка приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], содержащих параллельно выполняемые действия в средстве [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] более ранней версии. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 При отладке действий прежних версий, которые выполняются одновременно, таких как **ParallelActivity** или **ConditionedActivityGroup**, можно использовать один из следующих двух вариантов для пошаговой проверки кода .  
  
-   **Пошаговое выполнение ветви.** Этот режим проверки позволяет выполнить проверку и отладку определенной ветви сложного действия, такие как **ParallelActivity** или **ConditionalActivityGroup** действия. При использовании этого параметра для отладки будет заметно возникновение изменения в элементе управления из-за параллельного выполнения других действий в рабочем процессе. Отладчик выполняет проверку по шагам действий выбранной в данный момент ветви, тогда как другие действия в рабочем процессе могут выполняться параллельно. Например, по умолчанию, крайняя слева ветвь в **ParallelActivity** действия и первое дочернее действие **ConditionedActivityGroup** действия используются для проверки. Если нужно получить сведения об отладке любой другой ветви или дочернего действия, явная точка останова должна быть размещена в этой ветви или в дочернем действии. Проверка продолжается в этой ветви после запуска точки останова.  
  
-   **Пошаговое выполнение экземпляра.** Этот режим проверки позволяет выполнить проверку и отладку параллельно выполняемых действий в рабочем процессе. С этим параметром будет заметно возникновение изменения в элементе управления при параллельно выполняемых действиях, запущенных в рабочем процессе.  
  
 По умолчанию выбран вариант с пошаговым выполнением ветви. Пользователи могут переключаться между двумя этими вариантами при отладке рабочего процесса более ранней версии.  
  
 При отладке рабочих процессов конечного автомата более ранней версии необходимо выбрать режим проверки пошагового выполнения экземпляра.  
  
## <a name="see-also"></a>См. также  
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)   
 [Как изменить вариант пошаговой отладки (для прежних версий)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)