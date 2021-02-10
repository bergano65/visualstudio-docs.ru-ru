---
title: Конструктор действия CancellationScope
description: Узнайте, как можно использовать конструктор действий CancellationScope в конструктор рабочих процессов для создания и настройки действия CancellationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef415763a67232f79b269650abecfe6bcabe6bd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937203"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope

Конструктор действий **CancellationScope** используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope

Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope

Конструктор действия **CancellationScope** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор действий **CancellationScope** можно перетаскивать из **панели элементов** в область Конструктор рабочих процессов, где бы они ни находились, как в <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий **CancellationScope** создается <xref:System.Activities.Statements.CancellationScope> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Измените <xref:System.Activities.Activity.DisplayName%2A> значение в заголовке конструктора действий **CancellationScope** . Его также можно изменить в поле **DisplayName** сетки свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope

В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A>Свойство можно изменить в сетке свойств, но другие свойства необходимо изменить на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите действие из **области элементов** в поле **текст** в конструкторе действий **CancellationScope** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Указывает действие, выполняемое при отмене. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите действие из **области элементов** в поле **CancellationHandler** конструктора действий **CancellationScope** . Добавьте текст подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также раздел

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Уточнит](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
