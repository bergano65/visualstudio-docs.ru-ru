---
title: Конструктор действий по подтверждению конструктор рабочих процессов
description: Сведения о конструкторе действий Confirm и о том, как с помощью этого конструктора можно создать и настроить действие Confirm.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0227a300160434d0052e81d7c1ccd107c5a11a01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955662"
---
# <a name="confirm-activity-designer"></a>Конструктор действия Confirm

Конструктор действия **Confirm** используется для создания и настройки <xref:System.Activities.Statements.Confirm> действия.

## <a name="the-confirm-activity"></a>Действие Confirm
 Действие <xref:System.Activities.Statements.Confirm> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Confirm> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Confirm.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-confirm-activity-designer"></a>Использование конструктора действия Confirm
 Конструктор действия " **подтвердить** " можно найти в категории " **транзакция** " **панели элементов**, щелкнув вкладку " **область элементов** " в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

 Конструктор действия **Confirm** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.Confirm>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Confirm. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить либо в заголовке конструктора действий **Confirm** , либо в поле **DisplayName** сетки свойств.

### <a name="the-confirm-properties"></a>Свойства Confirm
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Confirm> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A>Свойство можно изменить в сетке свойств или на конструктор рабочих процессов поверхности, но <xref:System.Activities.Statements.Confirm.Target%2A> свойство должно быть изменено в сетке свойств.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию используется Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>См. также раздел

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)