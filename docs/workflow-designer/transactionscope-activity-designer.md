---
title: Конструктор рабочих процессов - конструктора операций TransactionScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67c8a5c610492f298d3f2ef6de35444c96f7310f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope

**TransactionScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TransactionScope> действия.

## <a name="the-transactionscope-activity"></a>Действие TransactionScope
 Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.

### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope
 **TransactionScope** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов**  конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **TransactionScope** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **TransactionScope** конструктора или в **DisplayName** поле сетки свойств.

### <a name="the-transactionscope-properties"></a>Свойства TransactionScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> И <xref:System.Activities.Statements.TransactionScope.Body%2A> свойства могут быть изменены на поверхности конструктора рабочих процессов. Но другие свойства следует изменять в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить <xref:System.Activities.Statements.TransactionScope.Body%2A> действие, перетащите действие из **элементов** в **текст** поле на **TransactionScope** конструктора действий с текстом подсказки «перетащить действие Сюда».|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Да|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Да|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Компенсации](../workflow-designer/compensate-activity-designer.md)
- [Подтверждение](../workflow-designer/confirm-activity-designer.md)