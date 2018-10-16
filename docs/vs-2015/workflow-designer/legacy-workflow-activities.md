---
title: Действия рабочего процесса прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205420"
---
# <a name="legacy-workflow-activities"></a>Действия с рабочими процессами для прежних версий
[!INCLUDE[wf](../includes/wf-md.md)] включает набор действий по умолчанию, которые предоставляют функции работы с потоками управления, условиями, обработки событий, управления состоянием и взаимодействия с приложениями и службами. При разработке рабочих процессов можно использовать действия, предоставляемые системой [!INCLUDE[wfd1](../includes/wfd1-md.md)], или создавать собственные пользовательские действия.  
  
 В следующей таблице приведен набор предопределенных действий среды [!INCLUDE[wf2](../includes/wf2-md.md)]. Многие, но не все из этих действий представлены конструкторами действий, которые может осуществляться из **элементов** из [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Чтобы создать действие, перетащите его конструктор из **элементов** и поместите его в рабочей области конструирования.  
  
|Действие|Описание|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Используется с **HandleExternalEventActivity** действия для входящих и исходящих взаимодействий с локальными службами. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Используется для хранения логики сложного действия, отмененного до завершения выполнения всех дочерних элементов составного действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Используется для добавления кода Visual Basic или C# в рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Допускающая компенсацию версия [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Допускающая компенсацию версия **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Позволяет вызвать код для отмены или компенсации операций, уже выполняемых рабочим процессом, при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[Действие CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Оболочка для одного или нескольких действий, которые выполняют компенсацию завершенного действия TransactionScopeActivity [!INCLUDE[crdefault](../includes/crdefault-md.md)] [использование действия CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Выполняет дочерние действия на основе условия, которое применяется к [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) само действие и на основе условий, которые применяются отдельно для каждого дочернего элемента. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Позволяет встроить в рабочий процесс задержку, которая основана на интервале тайм-аута. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Создает оболочку одного или нескольких действий, которые выполняются при возникновении заданного события. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Предоставляет среду для связывания событий с действием. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Выполняет основное дочернее действие одновременно с [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Используется для обработки исключения заданного типа. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Представляет составное действие, которое имеет упорядоченный список дочерних действий типа [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Используется в сочетании с [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) действия для входящих и исходящих взаимодействий с локальными службами. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Проверяет условие в каждой ветви и выполняет действия в первой ветви, для которой равняется условие **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Представляет ветвь действия [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Позволяет рабочему процессу вызывать веб-службу. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Позволяет рабочему процессу вызывать другой рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Составное действие, которое содержит только [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) дочерних действий. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Позволяет запланировать две или несколько дочерних **SequenceActivity** ветви действия для обработки в то же время. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Используется для представления коллекции правил. Правило состоит из условий и результирующих действий. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Создает несколько экземпляров одного дочернего действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Предоставляет простой способ для связи между собой нескольких операций для последовательного выполнения. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Задает переход к новому состоянию. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Представляет состояние в рабочем процессе конечного автомата. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Используется в [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) как контейнер для дочерних действий, выполняемых при выходе из **StateActivity** действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Используется в [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) как контейнер для дочерних действий, выполняемых при входе **StateActivity** действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Приостанавливает операцию рабочего процесса, чтобы позволить вмешательство при возникновении некоторой ошибки, которая требует особого внимания. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Выполняет содержащиеся действия последовательно в синхронизированном домене. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Позволяет немедленно завершить операцию рабочего процесса при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Позволяет захватить исключения бизнес-правил, возникающие как часть метаданных процесса для рабочего процесса. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Предоставляет среду для обработки транзакций и исключений. Дополнительные сведения см. в разделе [использование действия TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Предоставляет возможность смоделировать возникновение ошибки веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Получает данные из веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Отвечает на запрос веб-службы, сделанный рабочим процессом. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Разрешает цикл рабочего процесса до выполнения условия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Использование действия WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] как создать настраиваемые действия, см. в разделе [Разработка пользовательских действий](http://go.microsoft.com/fwlink?LinkID=65023) и [использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Представления действий (для прежних версий)](../workflow-designer/activity-views-legacy.md)  
 Описание различных представлений конструктора действий.  
  
 [Как добавить действия в область элементов (для прежних версий)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Рассматривается добавление действий на панель инструментов.  
  
 [Как создать условие декларативного правила (для прежних версий)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Последовательность действий для создания условия декларативного правила.  
  
 [Как создать набор правил PolicyActivity (для прежних версий)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Последовательность действий для создания набора правила PolicyActivity.  
  
 [Как реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Последовательность действий для реализации операции контракта [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
 [Как вызвать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Последовательность действий для вызова операции контракта [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Действия Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Разработка рабочих процессов](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Разработка действий рабочих процессов](http://go.microsoft.com/fwlink?LinkID=65023)