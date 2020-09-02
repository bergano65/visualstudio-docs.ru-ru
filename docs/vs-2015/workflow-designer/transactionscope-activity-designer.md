---
title: Конструктор действия TransactionScope | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670179"
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope
Конструктор действий **TransactionScope** используется для создания и настройки <xref:System.Activities.Statements.TransactionScope> действия.

## <a name="the-transactionscope-activity"></a>Действие TransactionScope
 Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.

### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope
 Конструктор операций **TransactionScope** можно найти в категории " **транзакция** " **панели элементов**, щелкнув вкладку " **область элементов** " в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выберите **панель инструментов** в меню " **вид** " или нажмите клавиши CTRL + ALT + X).

 Конструктор операций **TransactionScope** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора операций **TransactionScope** или в поле **DisplayName** сетки свойств.

### <a name="the-transactionscope-properties"></a>Свойства TransactionScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Но другие свойства следует изменять в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Верно|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить <xref:System.Activities.Statements.TransactionScope.Body%2A> действие, перетащите действие из **области элементов** в поле **текст** в конструкторе операций **TransactionScope** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Верно|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Неверно|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Верно|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|

## <a name="see-also"></a>См. также:
 [Transaction](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [компенсация](../workflow-designer/compensate-activity-designer.md) [Подтверждение](../workflow-designer/confirm-activity-designer.md)