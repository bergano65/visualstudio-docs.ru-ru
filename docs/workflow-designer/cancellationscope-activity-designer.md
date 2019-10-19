---
title: Конструктор действий конструктор рабочих процессов CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650706"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope

Конструктор действий **CancellationScope** используется для создания и настройки действия <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope

Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope

Конструктор действия **CancellationScope** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** +**ALT** +**X**.

Конструктор действий **CancellationScope** можно перетаскивать из **панели элементов** в область Конструктор рабочих процессов, где бы они ни находились, как в <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий **CancellationScope** создается действие <xref:System.Activities.Statements.CancellationScope> с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию CancellationScope. Измените значение <xref:System.Activities.Activity.DisplayName%2A> в заголовке конструктора действий **CancellationScope** . Его также можно изменить в поле **DisplayName** сетки свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope

В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в сетке свойств, но другие свойства необходимо изменить на поверхности конструктор рабочих процессов.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.Body%2A>, перетащите действие из **области элементов** в поле **текст** в конструкторе действий **CancellationScope** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Указывает действие, выполняемое при отмене. Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, перетащите действие из **области элементов** в поле **CancellationHandler** конструктора действий **CancellationScope** . Добавьте текст подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)