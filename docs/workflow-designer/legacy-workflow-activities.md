---
title: "Действия рабочего процесса прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ae0cef2943abffe947c179f9cfcd6c2223931337
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2018
---
# <a name="legacy-workflow-activities"></a>Действия с рабочими процессами для прежних версий
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] включает набор действий по умолчанию, которые предоставляют функции работы с потоками управления, условиями, обработки событий, управления состоянием и взаимодействия с приложениями и службами. При разработке рабочих процессов можно использовать действия, предоставляемые системой [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], или создавать собственные пользовательские действия.  
  
 В следующей таблице приведен набор предопределенных действий среды [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Многие, но не все из этих действий представлены конструкторами действий, которые можно получить доступ из **элементов** из [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Чтобы создать действие, перетащите его конструктор из **элементов** и поместите его в рабочей области конструирования.  
  
|Действие|Описание:|  
|--------------|-----------------|  
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|При использовании **HandleExternalEventActivity** действия для входящих и исходящих взаимодействий с локальными службами. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|**System.Workflow.Activities.CancellationHandlerActivity**|Используется для хранения логики сложного действия, отмененного до завершения выполнения всех дочерних элементов составного действия. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|<xref:System.Workflow.Activities.CodeActivity>|Используется для добавления кода Visual Basic или C# в рабочий процесс. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Используя действие CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Допускающая компенсацию версия действия <xref:System.Workflow.Activities.SequenceActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Допускающая компенсацию версия **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|**System.Workflow.Activities.CompensateActivity**|Позволяет вызвать код для отмены или компенсации операций, уже выполняемых рабочим процессом, при возникновении ошибки. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|**System.Workflow.Activities.CompensationHandlerActivity**|Программа-оболочка для одного или нескольких действий, которые выполняют компенсацию завершенного действия TransactionScopeActivity [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [использование действия CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Выполняет дочерние действия на основе условия, которое применяется к самому действию <xref:System.Workflow.Activities.ConditionedActivityGroup>, и на основе условий, которые применяются отдельно к каждому дочернему действию. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|<xref:System.Workflow.Activities.DelayActivity>|Позволяет встроить в рабочий процесс задержку, которая основана на интервале тайм-аута. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|<xref:System.Workflow.Activities.EventDrivenActivity>|Создает оболочку одного или нескольких действий, которые выполняются при возникновении заданного события. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|<xref:System.Workflow.Activities.EventHandlersActivity>|Предоставляет среду для связывания событий с действием. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Выполняет основное дочернее действие одновременно с <xref:System.Workflow.Activities.EventHandlersActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|**System.Workflow.Activities.FaultHandlerActivity**|Используется для обработки исключения заданного типа. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|**System.Workflow.Activities.FaultHandlersActivity**|Представляет составное действие, которое имеет упорядоченный список дочерних действий типа **System.Workflow.Activities.FaultHandlerActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Использовать в сочетании с <xref:System.Workflow.Activities.CallExternalMethodActivity> действия для входящих и исходящих взаимодействий с локальными службами. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|<xref:System.Workflow.Activities.IfElseActivity>|Проверяет условие в каждой ветви и выполняет действия в первой ветви, для которого условие равно **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Представляет ветвь действия <xref:System.Workflow.Activities.IfElseActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Позволяет рабочему процессу вызывать веб-службу. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Позволяет рабочему процессу вызывать другой рабочий процесс. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|<xref:System.Workflow.Activities.ListenActivity>|Составное действие, которое содержит только дочерние действия <xref:System.Workflow.Activities.EventDrivenActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия операция ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|<xref:System.Workflow.Activities.ParallelActivity>|Предоставляет способ для планирования двух или более дочерних **SequenceActivity** ветвей действия для обработки в то же время. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|<xref:System.Workflow.Activities.PolicyActivity>|Используется для представления коллекции правил. Правило состоит из условий и результирующих действий. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|<xref:System.Workflow.Activities.ReplicatorActivity>|Создает несколько экземпляров одного дочернего действия. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|<xref:System.Workflow.Activities.SequenceActivity>|Предоставляет простой способ для связи между собой нескольких операций для последовательного выполнения. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|<xref:System.Workflow.Activities.SetStateActivity>|Задает переход к новому состоянию. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|<xref:System.Workflow.Activities.StateActivity>|Представляет состояние в рабочем процессе конечного автомата. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Используется в <xref:System.Workflow.Activities.StateActivity> действия в качестве контейнера для дочерних действий, выполняемых при выходе из **StateActivity** действия. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|<xref:System.Workflow.Activities.StateInitializationActivity>|Используется в <xref:System.Workflow.Activities.StateActivity> действия в качестве контейнера для дочерних действий, выполняемых при входе **StateActivity** действия. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Используя действие StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**System.Workflow.Activities.SuspendActivity**|Приостанавливает операцию рабочего процесса, чтобы позволить вмешательство при возникновении некоторой ошибки, которая требует особого внимания. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия операция SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|**System.Workflow.Activities.SynchronizationScopeActivity**|Выполняет содержащиеся действия последовательно в синхронизированном домене. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|**System.Workflow.Activities.TerminateActivity**|Позволяет немедленно завершить операцию рабочего процесса при возникновении ошибки. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|**System.Workflow.Activities.ThrowActivity**|Позволяет захватить исключения бизнес-правил, возникающие как часть метаданных процесса для рабочего процесса. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|**System.Workflow.Activities.TransactionScopeActivity**|Предоставляет среду для обработки транзакций и исключений. Дополнительные сведения см. в разделе [использование действия TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Предоставляет возможность смоделировать возникновение ошибки веб-службы. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия операция WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Получает данные из веб-службы. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Отвечает на запрос веб-службы, сделанный рабочим процессом. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|<xref:System.Workflow.Activities.WhileActivity>|Разрешает цикл рабочего процесса до выполнения условия. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Использование действия у операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]способы создания пользовательских действий см. в разделе [Разработка пользовательских действий](http://go.microsoft.com/fwlink?LinkID=65023) и [использование конструктора действий прежних версий](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Представления действий (для прежних версий)](../workflow-designer/activity-views-legacy.md)  
 Описание различных представлений конструктора действий.  
  
 [Как добавить действия в область элементов (для прежних версий)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Рассматривается добавление действий на панель инструментов.  
  
 [Как создать условие декларативного правила (для прежних версий)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Последовательность действий для создания условия декларативного правила.  
  
 [Как создать набор правил PolicyActivity (для прежних версий)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Последовательность действий для создания набора правила PolicyActivity.  
  
 [Как: реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Последовательность действий для реализации операции контракта [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
 [Как: вызвать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Последовательность действий для вызова операции контракта [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
## <a name="see-also"></a>См. также  
 [Windows Workflow Foundation действий](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Разработка рабочих процессов](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Разработка действий рабочего процесса](http://go.microsoft.com/fwlink?LinkID=65023)