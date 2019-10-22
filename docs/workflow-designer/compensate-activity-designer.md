---
title: Конструктор действий компенсации конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650657"
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate

Конструктор действий **компенсации** используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.

## <a name="the-compensate-activity"></a>Действие Compensate

Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.

Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate

Конструктор действия **компенсации** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** +**ALT** +**X**.

Конструктор действий **компенсации** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где бы находились действия, например внутри <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий создается <xref:System.Activities.Statements.Compensate> действие с <xref:System.Activities.Activity.DisplayName%2A>ой компенсации по умолчанию. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **компенсации** или в поле **DisplayName** сетки свойств.

### <a name="the-compensate-properties"></a>Свойства Compensate

В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в сетке свойств или на поверхности конструктор рабочих процессов. Измените свойство <xref:System.Activities.Statements.Compensate.Target%2A> в сетке свойств.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Compensate>. Значение по умолчанию - Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Конструктор действия Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)