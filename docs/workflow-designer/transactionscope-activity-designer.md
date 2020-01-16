---
title: Конструктор действий TransactionScope конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef35457b9f28864929ad42919fff4e9afdcb0d5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114819"
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope

Конструктор действий **TransactionScope** используется для создания и настройки действия <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Действие TransactionScope

Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.

### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope

Доступ к конструктору операций **TransactionScope** в категории " **транзакция** " **панели элементов**. Конструктор операций **TransactionScope** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **TransactionScope** или в поле **DisplayName** сетки свойств.

### <a name="the-transactionscope-properties"></a>Свойства TransactionScope

В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить на поверхности конструктор рабочих процессов. Но другие свойства следует изменять в таблице свойств.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ложь|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Да|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить действие <xref:System.Activities.Statements.TransactionScope.Body%2A>, перетащите действие из **области элементов** в поле **текст** в конструкторе действия **TransactionScope** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Да|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Ложь|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|
|[System. Activity. Transactions. TransactionScope. AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Да|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|

## <a name="see-also"></a>См. также:

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
