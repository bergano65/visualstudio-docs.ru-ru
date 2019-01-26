---
title: Конструктор рабочих процессов - конструктор действия Confirm
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 483ac2b294ee68518313767576ed8c2e44301e83
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956952"
---
# <a name="confirm-activity-designer"></a>Конструктор действия Confirm

**Подтверждение** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Confirm> действия.

## <a name="the-confirm-activity"></a>Действие Confirm
 Действие <xref:System.Activities.Statements.Confirm> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Confirm> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Confirm.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-confirm-activity-designer"></a>Использование конструктора действия Confirm
 **Подтверждение** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов**вкладка в левой части конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

 **Подтверждение** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Confirm>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Confirm. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Подтверждение** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-confirm-properties"></a>Свойства Confirm
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Confirm> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> Свойство можно изменить в таблице свойств, а также на поверхности конструктора рабочих процессов, но <xref:System.Activities.Statements.Confirm.Target%2A> свойства необходимо изменить в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию используется Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)