---
title: Конструктор действия "подтвердить" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656966"
---
# <a name="confirm-activity-designer"></a>Конструктор действия Confirm
Конструктор действия **Confirm** используется для создания и настройки <xref:System.Activities.Statements.Confirm> действия.

## <a name="the-confirm-activity"></a>Действие Confirm
 Действие <xref:System.Activities.Statements.Confirm> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Confirm> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Confirm.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-confirm-activity-designer"></a>Использование конструктора действия Confirm
 Конструктор действия **Confirm** можно найти в категории **транзакция** **панели элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор действия **Confirm** можно перетащить из **области элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.Confirm>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Confirm. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить либо в заголовке конструктора действий **Confirm** , либо в поле **DisplayName** сетки свойств.

### <a name="the-confirm-properties"></a>Свойства Confirm
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Confirm> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../includes/wfd2-md.md)], однако свойство <xref:System.Activities.Statements.Confirm.Target%2A> можно изменить только в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию используется Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Верно|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>См. также:
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [reкомпенсации](../workflow-designer/compensate-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)