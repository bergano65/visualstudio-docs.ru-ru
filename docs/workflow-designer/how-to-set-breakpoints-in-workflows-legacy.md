---
title: "Способ: Установите точки останова в рабочих процессах (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d634f9648ed87f448e1b984392c827badc42930c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Как задать точки останова в рабочих процессах (для прежних версий)
В этом разделе описывается задание точек останова в приложениях [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], построенных с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий. Используйте средство [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий, если приложение [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] должно ориентироваться на [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 При использовании средства [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий в среде [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] для построения приложения [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] точки останова в коде на языке C# или Visual Basic можно задавать так же, как в Visual Studio. Как ожидалось, выполнение рабочего процесса останавливается в каждой заданной точке останова.  
  
 Точка останова имеет три состояния: *ожидающие*, *привязан*, и *ошибка*. При установке точки останова она имеет состояние Ожидание, которое представлено пустым красным значком. Когда среда выполнения загружает тип рабочего процесса, выполняется переход в состояние Привязка, которое представлено сплошным красным значком. Если задать неправильный формат для точки останова, как для неправильного имени действия, появляется окно сообщений об ошибке. Точка останова останется в окне точек останова, но будет отмечена маленьким «х».  
  
 Можно установить точки останова в действии в рабочей области конструктора рабочих процессов следующими способами:  
  
-   Щелкните правой кнопкой мыши действие и выберите **точка останова \ вставить точку останова**.  
  
-   Выделите действие и нажмите клавишу F9.  
  
-   Выберите **новую точку останова** из **отладки** меню.  
  
     Этот вариант также можно использовать для установки новой точки останова при отладке, когда отладчик останавливается в точке останова.  
  
    > [!NOTE]
    >  Задание точек останова в вызванных рабочих процессах не поддерживается.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Чтобы задать точку останова с использованием команды "Создать точку останова" из меню "Отладка"  
  
1.  На **отладки** последовательно выберите пункты **новую точку останова**.  
  
2.  Нажмите кнопку **прервать в функции**.  
  
     **Новую точку останова** откроется диалоговое окно.  
  
3.  Укажите имя действия в **функция** текстовое поле, используя следующий синтаксис: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Кроме того, вместо использования имени действия в **функция** текстовое поле, можно установить точку останова путем указания абсолютного пути действия рабочего процесса. Например, предположим, что у вас есть решение рабочего процесса с именем **WorkflowConsoleApplication1** и рабочий процесс в решении с именем **Workflow1** , использующий действие с именем **Delay1**. Можно использовать имя действия **Delay1** или указать путь **Delay1:WorkflowConsoleApplication1.Workflow1** или **Delay1:WorkflowConsoleApplication1.Workflow1: {} 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4.  Выберите **использовать технологию IntelliSense** флажок для проверки имени функции.  
  
     Если этот флажок не установлен, то проверка имени точки останова не выполняется.  
  
5.  Выберите **рабочего процесса** из **языка** списка.  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)   
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)