---
title: Конструктор рабочих процессов - конструктора операций Compensate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8278066a12df0d195770391d0b2f3144ba16487d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972271"
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate

**Compensate** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.

## <a name="the-compensate-activity"></a>Действие Compensate
 Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate
 **Compensate** конструктора действий можно найти в **транзакции** категории **элементов**. Чтобы открыть **элементов**выберите **элементов** вкладка в левой части конструктора рабочих процессов (либо выберите **инструментов** из **представление**меню или сочетание клавиш CTRL + ALT + X.)

 **Compensate** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Перемещение конструктора действий создает <xref:System.Activities.Statements.Compensate> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Compensate. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Compensate** конструктора или в **DisplayName** поле сетки свойств.

### <a name="the-compensate-properties"></a>Свойства Compensate
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> Свойство можно изменить в таблице свойств или на поверхности конструктора рабочих процессов. Изменить <xref:System.Activities.Statements.Compensate.Target%2A> свойства в сетке свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Compensate>. Значение по умолчанию - Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Конструктор действия Compensate](../workflow-designer/compensate-activity-designer.md)
- [Подтверждение](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)