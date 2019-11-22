---
title: Legacy Workflow Activities | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302960"
---
# <a name="legacy-workflow-activities"></a>Действия с рабочими процессами для прежних версий
[!INCLUDE[wf](../includes/wf-md.md)] включает набор действий по умолчанию, которые предоставляют функции работы с потоками управления, условиями, обработки событий, управления состоянием и взаимодействия с приложениями и службами. При разработке рабочих процессов можно использовать действия, предоставляемые системой [!INCLUDE[wfd1](../includes/wfd1-md.md)], или создавать собственные пользовательские действия.

 В следующей таблице приведен набор предопределенных действий среды [!INCLUDE[wf2](../includes/wf2-md.md)]. Many, but not all, of these activities are represented by activity designers that can be accessed from the **Toolbox** of the [!INCLUDE[wfd2](../includes/wfd2-md.md)]. To create an activity, drag its designer from the **Toolbox** and drop it on the design surface.

|Действие|Описание|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Used with the **HandleExternalEventActivity** activity for input and output communications with a local service. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CallExternalMethodActivity Activity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Используется для хранения логики сложного действия, отмененного до завершения выполнения всех дочерних элементов составного действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CancellationHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Используется для добавления кода Visual Basic или C# в рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CodeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|A compensatable version of [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensatableSequenceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|A compensatable version of **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensatableTransactionScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Позволяет вызвать код для отмены или компенсации операций, уже выполняемых рабочим процессом, при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|A wrapper for one or more activities that perform compensation for a completed TransactionScopeActivity activity [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensationHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Executes child activities based on a condition that applies to the [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) activity itself and based on conditions that apply separately to each child. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ConditionedActivityGroup Activity](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|Позволяет встроить в рабочий процесс задержку, которая основана на интервале тайм-аута. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the DelayActivity Activity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Создает оболочку одного или нескольких действий, которые выполняются при возникновении заданного события. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Предоставляет среду для связывания событий с действием. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventHandlersActivity Activity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Executes its main child activity concurrently with an [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventHandlingScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Используется для обработки исключения заданного типа. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the FaultHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Represents a composite activity that has an ordered list of child activities of type [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the FaultHandlersActivity Activity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Used in conjunction with the [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) activity for input and output communications with a local service. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the HandleExternalEventActivity Activity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Tests a condition on each branch and performs activities on the first branch for which the condition equals **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the IfElseActivity Activity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Represents a branch of an [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the IfElseBranchActivity Activity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Позволяет рабочему процессу вызывать веб-службу. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the InvokeWebServiceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Позволяет рабочему процессу вызывать другой рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the InvokeWorkflowActivity Activity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|A composite activity that contains only [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) child activities. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ListenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Provides a way to schedule two or more child **SequenceActivity** activity branches for processing at the same time. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ParallelActivity Activity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Используется для представления коллекции правил. Правило состоит из условий и результирующих действий. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Создает несколько экземпляров одного дочернего действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ReplicatorActivity Activity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Предоставляет простой способ для связи между собой нескольких операций для последовательного выполнения. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SequenceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Задает переход к новому состоянию. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Представляет состояние в рабочем процессе конечного автомата. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Used in a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity as a container for child activities that are executed when leaving the **StateActivity** activity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Used in a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity as a container for child activities that are executed when entering the **StateActivity** activity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Приостанавливает операцию рабочего процесса, чтобы позволить вмешательство при возникновении некоторой ошибки, которая требует особого внимания. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SuspendActivity Activity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Выполняет содержащиеся действия последовательно в синхронизированном домене. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SynchronizationScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Позволяет немедленно завершить операцию рабочего процесса при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the TerminateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|Позволяет захватить исключения бизнес-правил, возникающие как часть метаданных процесса для рабочего процесса. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ThrowActivity Activity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Предоставляет среду для обработки транзакций и исключений. For more information, see [Using the TransactionScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Предоставляет возможность смоделировать возникновение ошибки веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceFaultActivity Activity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Получает данные из веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceInputActivity Activity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Отвечает на запрос веб-службы, сделанный рабочим процессом. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceOutputActivity Activity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Разрешает цикл рабочего процесса до выполнения условия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WhileActivity Activity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] how to create custom activities, see [Developing Custom Activities](https://go.microsoft.com/fwlink?LinkID=65023) and [Using the Legacy Activity Designer](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Содержание
 [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md) Describes the different design views of activities.

 [How to: Add Activities to the Toolbox (Legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Shows how to add activities to the toolbox.

 [How to: Create a Declarative Rule Condition (Legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Shows the steps to create a declarative rule condition.

 [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Shows the steps to create a PolicyActivity rule set.

 [How to: Implement a WCF Contract Operation (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Shows the steps to implement a [!INCLUDE[indigo2](../includes/indigo2-md.md)] contract operation.

 [How to: Invoke a WCF Contract Operation (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Shows the steps to invoke a [!INCLUDE[indigo2](../includes/indigo2-md.md)] contract operation.

## <a name="see-also"></a>См. также раздел
 [Windows Workflow Foundation Activities](https://go.microsoft.com/fwlink?LinkID=65005) [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010) [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65023)