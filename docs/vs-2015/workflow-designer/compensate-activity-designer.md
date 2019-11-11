---
title: Конструктор действий компенсации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656979"
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate
Конструктор действий **компенсации** используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.

## <a name="the-compensate-activity"></a>Действие Compensate
 Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate
 Конструктор действий **компенсации** можно найти в категории **транзакция** **панели элементов**, щелкнув вкладку **область элементов** в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выбрать **панель инструментов** **в меню** Меню "вид" или CTRL + ALT + X.)

 Конструктор действий **компенсации** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Compensate> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Compensate. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **компенсации** или в поле **DisplayName** сетки свойств.

### <a name="the-compensate-properties"></a>Свойства Compensate
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../includes/wfd2-md.md)], однако свойство <xref:System.Activities.Statements.Compensate.Target%2A> можно изменить только в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Compensate>. Значение по умолчанию - Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Да|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>См. также
 Конструктор операций [компенсации](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [действия](../workflow-designer/compensate-activity-designer.md) [подтвердить](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)