---
title: Конструктор рабочих процессов - конструктор действия CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4194ef3d4cfbf4b4654b1695c022d715fc7d885
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857929"
---
# <a name="compensableactivity-activity-designer"></a>Конструктор действия CompensableActivity

**CompensableActivity** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CompensableActivity> действия.

## <a name="the-compensableactivity-activity"></a>Действие CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> определяет единицу работы, которая может быть подтверждена или компенсирована после успешного завершения.

### <a name="using-the-compensableactivity-activity-designer"></a>Использование конструктора действия CompensableActivity
 **CompensableActivity** конструктора действий можно найти в **транзакции** категории **элементов**. Чтобы открыть **элементов**выберите **элементов** вкладка в левой части конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

 **CompensableActivity** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов. Можно перетащить конструктор действия внутри <xref:System.Activities.Statements.Sequence>. Удаление конструктора действий создает <xref:System.Activities.Statements.CompensableActivity> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> действия compensableactivity будет иметь. Изменить <xref:System.Activities.Activity.DisplayName%2A> значение в заголовке **CompensableActivity** конструктора действий. Также можно изменить в **DisplayName** поле таблицы свойств.

### <a name="the-compensableactivity-properties"></a>Свойства CompensableActivity
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CompensableActivity> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A> И <xref:System.Activities.Activity%601.Result%2A> свойства можно изменить в таблице свойств, но другие свойства следует изменять в области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CompensableActivity>. Значение по умолчанию - CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Указывает возвращаемое значение <xref:System.Activities.Statements.CompensableActivity>. Это свойство необходимо изменять в таблице свойств.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Указывает действие, для которого производится компенсация, отмена и логика подтверждения. Чтобы добавить <xref:System.Activities.Statements.CompensableActivity.Body%2A> действие, перетащите его из **элементов** в **текст** поле на **CompensableActivity** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Указывает действие, выполняемое при отмене. Чтобы добавить действие, перетащите его конструктор из **элементов** в **CancellationHandler** поле **CompensableActivity** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Указывает выполняемое действие при компенсации для действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Compensate>.<br /><br /> Чтобы добавить действие, перетащите его конструктор из **элементов** в **CompensationHandler** поле **CompensableActivity** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Указывает действие, выполняемое при подтверждении действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Confirm>.<br /><br /> Чтобы добавить действие, перетащите его конструктор из **элементов** в **ConfirmationHandler** поле **CompensableActivity** конструктора действий. Добавьте текстом подсказки «Перетащить действие сюда».|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)