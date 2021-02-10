---
title: Конструктор действия CompensableActivity
description: Узнайте, как можно использовать конструктор действий CompensableActivity в конструктор рабочих процессов для создания и настройки действия CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9612e1b8e808437122df88ad0bbef3a4cce74c0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955116"
---
# <a name="compensableactivity-activity-designer"></a>Конструктор действия CompensableActivity

Конструктор действий **CompensableActivity** используется для создания и настройки <xref:System.Activities.Statements.CompensableActivity> действия.

## <a name="the-compensableactivity-activity"></a>Действие CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> определяет единицу работы, которая может быть подтверждена или компенсирована после успешного завершения.

### <a name="using-the-compensableactivity-activity-designer"></a>Использование конструктора действия CompensableActivity
 Конструктор действия **CompensableActivity** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

 Конструктор действий **CompensableActivity** можно перетащить из **области элементов** в область Конструктор рабочих процессов. Конструктор действий можно удалить внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.CompensableActivity> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity. Измените <xref:System.Activities.Activity.DisplayName%2A> значение в заголовке конструктора действий **CompensableActivity** . Его также можно изменить в поле **DisplayName** сетки свойств.

### <a name="the-compensableactivity-properties"></a>Свойства CompensableActivity
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CompensableActivity> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A>Свойство и <xref:System.Activities.Activity%601.Result%2A> можно изменить в сетке свойств, но другие свойства необходимо изменить на поверхности конструктор рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CompensableActivity>. Значение по умолчанию - CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Указывает возвращаемое значение <xref:System.Activities.Statements.CompensableActivity>. Это свойство необходимо изменять в таблице свойств.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Указывает действие, для которого производится компенсация, отмена и логика подтверждения. Чтобы добавить <xref:System.Activities.Statements.CompensableActivity.Body%2A> действие, перетащите действие из **области элементов** в поле **текст** в конструкторе действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Указывает действие, выполняемое при отмене. Чтобы добавить действие, перетащите его конструктор из **области элементов** в поле **CancellationHandler** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Указывает выполняемое действие при компенсации для действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Compensate>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Компенсатионхандлер** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Указывает действие, выполняемое при подтверждении действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Confirm>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Конфирматионхандлер** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также раздел

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Уточнит](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
