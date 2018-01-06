---
title: "Отладка рабочих процессов прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d15236de90af6a8749482f2b159d66c28a1b8c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-legacy-workflows"></a>Отладка рабочих процессов прежних версий
При использовании средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий в среде [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] для сборки приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], предназначенных для платформы .NET Framework 3.0 или 3.5, можно выполнять отладку рабочих процессов так же, как других программ, путем установки точек останова, присоединения к процессам, оценки потоков и стека вызова. Кроме того, существует возможность удаленной отладки.  
  
> [!NOTE]
>  Если на компьютере было установлено и удалено несколько версий Visual Studio, отладка WF3 может завершиться ошибкой по одной из следующих причин.  
>   
>  -   Не достигаются точки останова.  
> -   Отображается следующее сообщение:  
>   
>  **Не удается запустить отладку на веб-сервере. Отладчик не установлен должным образом.  Не удается отладить запрошенный тип кода.  Запустите программу установки для установки или восстановления отладчика.**  
>   
>  Если один из этих сценариев возникает при отладке рабочего процесса .NET Framework 3.0 или 3.5, выполните исправление установки Visual Studio.  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] интегрируется со следующими стандартными окнами отладки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   **Точка останова**: работает, как предполагалось, но задавать действия для имени функции.  
  
-   **Стек вызовов**: изменено, чтобы предоставить структуру действий, выполненных в экземпляре рабочего процесса. Записи в **стек вызовов** окна — это поиск в глубину по выполняющимся действиям. Можно дважды щелкнуть по записи, чтобы поместить фокус на выбранное действие.  
  
-   **Потоки**: предоставляет идентификатор экземпляра рабочего процесса, отлаживаемого экземпляра.  
  
 Visual Studio для Windows Workflow Foundation не поддерживает следующие возможности отладки:  
  
-   Условные точки останова на рабочей области конструктора операций.  
  
-   "Быстрая проверка".  
  
-   Задать следующий оператор.  
  
-   Выполнять до текущей позиции.  
  
-   Изменить и продолжить.  
  
-   JIT-отладка.  
  
-   Отладка в смешанном режиме.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Как отлаживать рабочие процессы, основанные на ASP.NET (для прежних версий)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Как задать точки останова в рабочих процессах (для прежних версий)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Отладка рабочих процессов с удаленного компьютера (для прежних версий)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Варианты пошаговой отладки (для прежних версий)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Как изменить вариант пошаговой отладки (для прежних версий)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)