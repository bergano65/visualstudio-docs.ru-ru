---
title: Конструктор действий компенсации конструктор рабочих процессов
description: Сведения о конструкторе действий компенсации и использовании конструктора действий компенсации для создания и настройки действия компенсации.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36ab20854adb952d098f71904cdd3cb092e27ac9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955688"
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate

Конструктор действий **компенсации** используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.

## <a name="the-compensate-activity"></a>Действие Compensate

Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.

Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate

Конструктор действия **компенсации** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор действий **компенсации** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где бы находились действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.Compensate> действие с параметром компенсации по умолчанию <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **компенсации** или в поле **DisplayName** сетки свойств.

### <a name="the-compensate-properties"></a>Свойства Compensate

В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A>Свойство можно изменить в сетке свойств или на конструктор рабочих процессов поверхности. Измените <xref:System.Activities.Statements.Compensate.Target%2A> свойство в сетке свойств.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Compensate>. Значение по умолчанию - Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>См. также раздел

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Конструктор действия Compensate](../workflow-designer/compensate-activity-designer.md)
- [Уточнит](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)