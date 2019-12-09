---
title: Устаревшие действия рабочего процесса | Документация Майкрософт
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
[!INCLUDE[wf](../includes/wf-md.md)] включает набор действий по умолчанию, которые предоставляют функциональные возможности для потока управления, условий, обработки событий, управления состоянием и взаимодействия с приложениями и службами. При разработке рабочих процессов можно использовать действия, предоставляемые системой [!INCLUDE[wfd1](../includes/wfd1-md.md)], или создавать собственные пользовательские действия.

 В следующей таблице приведен набор предопределенных действий среды [!INCLUDE[wf2](../includes/wf2-md.md)]. Многие, но не все эти действия представлены конструкторами действий, к которым можно получить доступ из **области элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Чтобы создать действие, перетащите его конструктор из **панели элементов** и поместите его в область конструктора.

|Действие|Описание|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Используется с действием **HandleExternalEventActivity** для обмена данными и вывода данных с локальной службой. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Используется для хранения логики сложного действия, отмененного до завершения выполнения всех дочерних элементов составного действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Используется для добавления кода Visual Basic или C# в рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[компенсатаблесекуенцеактивити](https://go.microsoft.com/fwlink?LinkID=65027)|Компенсируемые версия [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия компенсатаблесекуенцеактивити](https://go.microsoft.com/fwlink?LinkID=65002).|
|[компенсатаблетрансактионскопеактивити](https://go.microsoft.com/fwlink?LinkID=65051)|Компенсируемые версия **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия компенсатаблетрансактионскопеактивити](https://go.microsoft.com/fwlink?LinkID=65063).|
|[компенсатеактивити](https://go.microsoft.com/fwlink?LinkID=65052)|Позволяет вызвать код для отмены или компенсации операций, уже выполняемых рабочим процессом, при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия компенсатеактивити](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Оболочка для одного или нескольких действий, выполняющих компенсацию для завершенного действия TransactionScopeActivity [!INCLUDE[crdefault](../includes/crdefault-md.md)][помощью действия CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Выполняет дочерние действия на основе условия, которое применяется к самому действию [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) и на основе условий, которые применяются отдельно к каждому дочернему элементу. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[делайактивити](https://go.microsoft.com/fwlink?LinkID=65028)|Позволяет встроить в рабочий процесс задержку, которая основана на интервале тайм-аута. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия делайактивити](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Создает оболочку одного или нескольких действий, которые выполняются при возникновении заданного события. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[евенсандлерсактивити](https://go.microsoft.com/fwlink?LinkID=65018)|Предоставляет среду для связывания событий с действием. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия евенсандлерсактивити](https://go.microsoft.com/fwlink?LinkID=65069).|
|[евенсандлингскопеактивити](https://go.microsoft.com/fwlink?LinkID=65030)|Выполняет свою основную дочернюю операцию параллельно с [евенсандлерсактивити](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия евенсандлингскопеактивити](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Используется для обработки исключения заданного типа. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Представляет составное действие, имеющее упорядоченный список дочерних действий типа [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Используется в сочетании с действием [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) для обмена данными с локальной службой. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Проверяет условие в каждой ветви и выполняет действия в первой ветви, для которой условие равно **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Представляет ветвь [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[инвокевебсервицеактивити](https://go.microsoft.com/fwlink?LinkID=65035)|Позволяет рабочему процессу вызывать веб-службу. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия инвокевебсервицеактивити](https://go.microsoft.com/fwlink?LinkID=65076).|
|[инвокеворкфловактивити](https://go.microsoft.com/fwlink?LinkID=65036)|Позволяет рабочему процессу вызывать другой рабочий процесс. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия инвокеворкфловактивити](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|Составное действие, которое содержит только дочерние действия [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия ListenActivity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Предоставляет способ планирования двух или более дочерних ветвей действия **SequenceActivity** для обработки одновременно. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Используется для представления коллекции правил. Правило состоит из условий и результирующих действий. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Создает несколько экземпляров одного дочернего действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Предоставляет простой способ для связи между собой нескольких операций для последовательного выполнения. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Задает переход к новому состоянию. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Представляет состояние в рабочем процессе конечного автомата. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Используется в действии [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) в качестве контейнера для дочерних действий, выполняемых при закрытии действия **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Используется в действии [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) в качестве контейнера для дочерних действий, выполняемых при входе в действие **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[суспендактивити](https://go.microsoft.com/fwlink?LinkID=65056)|Приостанавливает операцию рабочего процесса, чтобы позволить вмешательство при возникновении некоторой ошибки, которая требует особого внимания. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия суспендактивити](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Выполняет содержащиеся действия последовательно в синхронизированном домене. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Позволяет немедленно завершить операцию рабочего процесса при возникновении ошибки. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[сровактивити](https://go.microsoft.com/fwlink?LinkID=65059)|Позволяет захватить исключения бизнес-правил, возникающие как часть метаданных процесса для рабочего процесса. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия сровактивити](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Предоставляет среду для обработки транзакций и исключений. Дополнительные сведения см. [в разделе Использование действия TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[Операция webservicefaultactivity](https://go.microsoft.com/fwlink?LinkID=65046)|Предоставляет возможность смоделировать возникновение ошибки веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия операция webservicefaultactivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Получает данные из веб-службы. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[Операция WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Отвечает на запрос веб-службы, сделанный рабочим процессом. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия операция WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Разрешает цикл рабочего процесса до выполнения условия. [!INCLUDE[crdefault](../includes/crdefault-md.md)][с помощью действия WhileActivity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] создании настраиваемых действий см. в разделе [Разработка настраиваемых действий](https://go.microsoft.com/fwlink?LinkID=65023) и [использование устаревшего конструктора действий](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>В этом разделе
 [Представления действий (прежние версии)](../workflow-designer/activity-views-legacy.md) Описание различных представлений конструктора действий.

 [Как добавить действия на панель элементов (прежние версии)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Показывает, как добавлять действия на панель элементов.

 [Как создать условие декларативного правила (для прежних версий)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Описание действий по созданию условия декларативного правила.

 [Как создать набор правил PolicyActivity (для прежних версий)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Описание действий по созданию набора правил PolicyActivity.

 [Как реализовать операцию контракта WCF (устаревшая)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Показывает действия по реализации [!INCLUDE[indigo2](../includes/indigo2-md.md)] контракта.

 [Как вызвать операцию контракта WCF (устаревшая)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Показывает шаги для вызова операции контракта [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>См. также
 [Windows Workflow Foundation действия](https://go.microsoft.com/fwlink?LinkID=65005) [Разработка рабочих процессов](https://go.microsoft.com/fwlink?LinkID=65010) [Разработка действий рабочего процесса](https://go.microsoft.com/fwlink?LinkID=65023)