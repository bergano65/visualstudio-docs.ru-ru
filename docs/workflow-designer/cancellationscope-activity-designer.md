---
title: Конструктор рабочих процессов - конструктор действия CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43a818be208c7e07ef74a8f35923f3042bb8fad5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938167"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope

**CancellationScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope

Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope

**CancellationScope** конструктора действий можно найти в **транзакции** категории **элементов**. Чтобы открыть **элементов**выберите **элементов** вкладке конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**CancellationScope** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление **CancellationScope** конструктора действий создает <xref:System.Activities.Statements.CancellationScope> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. Изменить <xref:System.Activities.Activity.DisplayName%2A> значение в заголовке **CancellationScope** конструктора действий. Вы также можете изменить его в **DisplayName** поле таблицы свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope

В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> Свойства можно изменить в таблице свойств, но другие свойства следует изменять в поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите его из **элементов** в **текст** поле на **CancellationScope** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Да|Указывает действие, выполняемое, если имеется отмены. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите его из **элементов** в **CancellationHandler** поле **CancellationScope** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)