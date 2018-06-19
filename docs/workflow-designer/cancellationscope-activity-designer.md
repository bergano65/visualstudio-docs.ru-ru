---
title: Конструктор рабочих процессов - конструктора операций CancellationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975345"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope

**CancellationScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope
 **CancellationScope** конструктора действий можно найти в **транзакции** категории **элементов**. Чтобы открыть **элементов**выберите **элементов** вкладки конструктора рабочих процессов. Можно также выбрать **инструментов** из **представление** меню или нажмите клавиши CTRL + ALT + X.

 **CancellationScope** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление **CancellationScope** создает конструктор действия <xref:System.Activities.Statements.CancellationScope> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. Изменить <xref:System.Activities.Activity.DisplayName%2A> значение в заголовке **CancellationScope** конструктора действий. Вы также можете изменить его в **DisplayName** поле сетки свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> Свойства можно изменить в таблице свойств, но другие свойства следует изменять в области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите действие из **элементов** в **текст** поле на **CancellationScope** конструктора действий. Добавьте текст подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Да|Указывает действие, выполняемое, если Отмена. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите действие из **элементов** в **CancellationHandler** поле на **CancellationScope** конструктора действий. Добавьте текст подсказки «Перетащить действие сюда».|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Компенсации](../workflow-designer/compensate-activity-designer.md)
- [Подтверждение](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)