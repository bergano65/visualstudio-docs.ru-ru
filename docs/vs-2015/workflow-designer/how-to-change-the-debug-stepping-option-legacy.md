---
title: Как изменить параметр пошаговой отладки (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663440"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Как изменить вариант пошаговой отладки (для прежних версий)
В этом разделе описывается изменение варианта пошаговой отладки для приложений [!INCLUDE[wf](../includes/wf-md.md)] прежних версий [!INCLUDE[wfd1](../includes/wfd1-md.md)] с параллельными действиями. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 При отладке устаревших действий с параллельным выполнением, например **ParallelActivity** или **ConditionedActivityGroup**, можно использовать один из двух вариантов для пошагового выполнения кода.

 Выполните следующие действия, чтобы изменить вариант пошаговой отладки в проекте рабочего процесса прежних версий.

## <a name="procedures"></a>Процедуры

#### <a name="to-change-the-debug-stepping-option"></a>Изменение варианта пошаговой отладки

1. Запустите Visual Studio.

2. Откройте существующий проект рабочего процесса прежних версий или создайте новый проект, в котором применяются параллельные действия и который предназначен для работы с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

3. В меню **Рабочий процесс** в списке устаревшие [!INCLUDE[wfd2](../includes/wfd2-md.md)] наведите указатель на пункт **Отладка**и выберите пункт **параметры шага**.

4. Выберите **экземпляр** или **ветвь**.

## <a name="see-also"></a>См. также:
 [Отладка устаревших рабочих процессов](../workflow-designer/debugging-legacy-workflows.md) [Отладка параметров пошагового выполнения (прежние версии)](../workflow-designer/debug-stepping-options-legacy.md)