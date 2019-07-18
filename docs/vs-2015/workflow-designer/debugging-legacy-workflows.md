---
title: Отладка рабочих процессов для прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 80edcfb171e8e87c384a05b889a8fa11b1e7a723
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439195"
---
# <a name="debugging-legacy-workflows"></a>Отладка рабочих процессов прежних версий
При использовании средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий в среде [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для сборки приложений [!INCLUDE[wf](../includes/wf-md.md)], предназначенных для платформы .NET Framework 3.0 или 3.5, можно выполнять отладку рабочих процессов так же, как других программ, путем установки точек останова, присоединения к процессам, оценки потоков и стека вызова. Кроме того, существует возможность удаленной отладки.  
  
> [!NOTE]
> Если на компьютере было установлено и удалено несколько версий Visual Studio, отладка WF3 может завершиться ошибкой по одной из следующих причин.  
> 
> - Не достигаются точки останова.  
>   - Отображается следующее сообщение:  
> 
>   **Не удается запустить отладку на веб-сервере. Отладчик не установлен должным образом.  Не удается отладить запрошенный тип кода.  Запустите программу установки для установки или восстановления отладчика.**  
> 
>   Если один из этих сценариев возникает при отладке рабочего процесса .NET Framework 3.0 или 3.5, выполните исправление установки Visual Studio.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] интегрируется со следующими стандартными окнами отладки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
- **Точка останова**: Работает, как ожидалось, но указать действие для имени функции.  
  
- **Стек вызовов**: Изменения, чтобы предоставить структуру действий, которые были выполнены в экземпляре рабочего процесса. Записи в **стек вызовов** окна являются преимущественно в глубину поиска выполняемых действий. Можно дважды щелкнуть по записи, чтобы поместить фокус на выбранное действие.  
  
- **Потоки**: Предоставляет идентификатор экземпляра для экземпляра рабочего процесса, отлаживаемого в.  
  
  Visual Studio для Windows Workflow Foundation не поддерживает следующие возможности отладки:  
  
- Условные точки останова на рабочей области конструктора операций.  
  
- "Быстрая проверка".  
  
- Задать следующий оператор.  
  
- Выполнять до текущей позиции.  
  
- Изменить и продолжить.  
  
- JIT-отладка.  
  
- Отладка в смешанном режиме.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Практическое руководство. Отладка рабочих процессов, основанных на ASP.NET (для прежних версий)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Практическое руководство. Задание точек останова в рабочих процессах (для прежних версий)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Отладка рабочих процессов с удаленного компьютера (для прежних версий)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Варианты пошаговой отладки (для прежних версий)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Практическое руководство. Изменение варианта пошаговой отладки (для прежних версий)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)