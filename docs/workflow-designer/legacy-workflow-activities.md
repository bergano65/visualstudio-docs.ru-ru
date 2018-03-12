---
title: "Действия рабочего процесса прежних версий | Документы Microsoft"
ms.date: 01/18/2017
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 61c719725f3d4ebfffe291ff31115ddd0cc5f3d4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="legacy-workflow-activities"></a>Действия с рабочими процессами для прежних версий

[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] включает набор действий по умолчанию, которые предоставляют функции работы с потоками управления, условиями, обработки событий, управления состоянием и взаимодействия с приложениями и службами. При разработке рабочих процессов, можно использовать системные действия, предоставляемые конструктором рабочих процессов Windows, или можно создать собственные пользовательские действия.

 В следующей таблице приведен набор предопределенных действий среды [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Многие, но не все из этих действий представлены конструкторами действий, которые можно получить доступ из **элементов** из [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Чтобы создать действие, перетащите его конструктор из **элементов** и поместите его в рабочей области конструирования.

|Действие|Описание:|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|При использовании **HandleExternalEventActivity** действия для входящих и исходящих взаимодействий с локальными службами. Дополнительные сведения см. в разделе [использование действия CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Используется для хранения логики сложного действия, отмененного до завершения выполнения всех дочерних элементов составного действия. Дополнительные сведения см. в разделе [использование действия CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Используется для добавления кода Visual Basic или C# в рабочий процесс. Дополнительные сведения см. в разделе [использование действия CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Допускающая компенсацию версия действия <xref:System.Workflow.Activities.SequenceActivity>. Дополнительные сведения см. в разделе [использование действия CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Допускающая компенсацию версия **TransactionScopeActivity**. Дополнительные сведения см. в разделе [использование действия CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Позволяет вызвать код для отмены или компенсации операций, уже выполняемых рабочим процессом, при возникновении ошибки. Дополнительные сведения см. в разделе [использование действия CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Программа-оболочка для одного или нескольких действий, которые выполняют компенсацию завершенного действия TransactionScopeActivity Дополнительные сведения см. в разделе [использование действия CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Выполняет дочерние действия на основе условия, которое применяется к самому действию <xref:System.Workflow.Activities.ConditionedActivityGroup>, и на основе условий, которые применяются отдельно к каждому дочернему действию. Дополнительные сведения см. в разделе [использование действия ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Позволяет встроить в рабочий процесс задержку, которая основана на интервале тайм-аута. Дополнительные сведения см. в разделе [использование действия DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Создает оболочку одного или нескольких действий, которые выполняются при возникновении заданного события. Дополнительные сведения см. в разделе [использование действия EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Предоставляет среду для связывания событий с действием. Дополнительные сведения см. в разделе [использование действия EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Выполняет основное дочернее действие одновременно с <xref:System.Workflow.Activities.EventHandlersActivity>. Дополнительные сведения см. в разделе [использование действия EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Используется для обработки исключения заданного типа. Дополнительные сведения см. в разделе [использование действия FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Представляет составное действие, которое имеет упорядоченный список дочерних действий типа **System.Workflow.Activities.FaultHandlerActivity**. Дополнительные сведения см. в разделе [использование действия FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Использовать в сочетании с <xref:System.Workflow.Activities.CallExternalMethodActivity> действия для входящих и исходящих взаимодействий с локальными службами. Дополнительные сведения см. в разделе [использование действия HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Проверяет условие в каждой ветви и выполняет действия в первой ветви, для которого условие равно **true**. Дополнительные сведения см. в разделе [использование действия IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Представляет ветвь действия <xref:System.Workflow.Activities.IfElseActivity>. Дополнительные сведения см. в разделе [использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Позволяет рабочему процессу вызывать веб-службу. Дополнительные сведения см. в разделе [использование действия InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Позволяет рабочему процессу вызывать другой рабочий процесс. Дополнительные сведения см. в разделе [использование действия InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Составное действие, которое содержит только дочерние действия <xref:System.Workflow.Activities.EventDrivenActivity>. Дополнительные сведения см. в разделе [использование действия операция ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Предоставляет способ для планирования двух или более дочерних **SequenceActivity** ветвей действия для обработки в то же время. Дополнительные сведения см. в разделе [использование действия ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|Используется для представления коллекции правил. Правило состоит из условий и результирующих действий. Дополнительные сведения см. в разделе [использование действия PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Создает несколько экземпляров одного дочернего действия. Дополнительные сведения см. в разделе [использование действия ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Предоставляет простой способ для связи между собой нескольких операций для последовательного выполнения. Дополнительные сведения см. в разделе [использование действия SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Задает переход к новому состоянию. Дополнительные сведения см. в разделе [использование действия SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Представляет состояние в рабочем процессе конечного автомата. Дополнительные сведения см. в разделе [использование действия StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Используется в <xref:System.Workflow.Activities.StateActivity> действия в качестве контейнера для дочерних действий, выполняемых при выходе из **StateActivity** действия. Дополнительные сведения см. в разделе [использование действия StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Используется в <xref:System.Workflow.Activities.StateActivity> действия в качестве контейнера для дочерних действий, выполняемых при входе **StateActivity** действия. Дополнительные сведения см. в разделе [с помощью действие StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Приостанавливает операцию рабочего процесса, чтобы позволить вмешательство при возникновении некоторой ошибки, которая требует особого внимания. Дополнительные сведения см. в разделе [использование действия операция SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Выполняет содержащиеся действия последовательно в синхронизированном домене. Дополнительные сведения см. в разделе [использование действия SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Позволяет немедленно завершить операцию рабочего процесса при возникновении ошибки. Дополнительные сведения см. в разделе [использование действия TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Позволяет захватить исключения бизнес-правил, возникающие как часть метаданных процесса для рабочего процесса. Дополнительные сведения см. в разделе [использование действия ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Предоставляет среду для обработки транзакций и исключений. Дополнительные сведения см. в разделе [использование действия TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Предоставляет возможность смоделировать возникновение ошибки веб-службы. Дополнительные сведения см. в разделе [использование действия операция WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Получает данные из веб-службы. Дополнительные сведения см. в разделе [использование действия WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Отвечает на запрос веб-службы, сделанный рабочим процессом. Дополнительные сведения см. в разделе [использование действия WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Разрешает цикл рабочего процесса до выполнения условия. Дополнительные сведения см. в разделе [использование действия у операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

 Дополнительные сведения о создании настраиваемых действий см. в разделе [Разработка пользовательских действий](http://go.microsoft.com/fwlink?LinkID=65023) и [использование конструктора действий прежних версий](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>См. также

- [Windows Workflow Foundation действий](http://go.microsoft.com/fwlink?LinkID=65005)
- [Разработка рабочих процессов](http://go.microsoft.com/fwlink?LinkID=65010)
- [Разработка действий рабочего процесса](http://go.microsoft.com/fwlink?LinkID=65023)