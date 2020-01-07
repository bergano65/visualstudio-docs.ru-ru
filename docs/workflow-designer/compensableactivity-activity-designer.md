---
title: Конструктор действий конструктор рабочих процессов CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597104"
---
# <a name="compensableactivity-activity-designer"></a>Конструктор действия CompensableActivity

Конструктор действий **CompensableActivity** используется для создания и настройки действия <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Действие CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> определяет единицу работы, которая может быть подтверждена или компенсирована после успешного завершения.

### <a name="using-the-compensableactivity-activity-designer"></a>Использование конструктора действия CompensableActivity
 Конструктор действия **CompensableActivity** можно найти в категории " **транзакция** " **панели элементов**. Чтобы открыть **панель элементов**, выберите вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL**+**ALT**+**X**.

 Конструктор действий **CompensableActivity** можно перетащить из **области элементов** в область Конструктор рабочих процессов. Конструктор действий можно удалить в <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий создается <xref:System.Activities.Statements.CompensableActivity> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию CompensableActivity. Измените значение <xref:System.Activities.Activity.DisplayName%2A> в заголовке конструктора действий **CompensableActivity** . Его также можно изменить в поле **DisplayName** сетки свойств.

### <a name="the-compensableactivity-properties"></a>Свойства CompensableActivity
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CompensableActivity> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Activity%601.Result%2A> можно изменить в сетке свойств, но другие свойства должны быть изменены на поверхности конструктор рабочих процессов.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ложь|Необязательное понятное имя действия <xref:System.Activities.Statements.CompensableActivity>. Значение по умолчанию - CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Ложь|Указывает возвращаемое значение <xref:System.Activities.Statements.CompensableActivity>. Это свойство необходимо изменять в таблице свойств.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Да|Указывает действие, для которого производится компенсация, отмена и логика подтверждения. Чтобы добавить действие <xref:System.Activities.Statements.CompensableActivity.Body%2A>, перетащите действие из **области элементов** в поле **текст** в конструкторе действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Ложь|Указывает действие, выполняемое при отмене. Чтобы добавить действие, перетащите его конструктор из **области элементов** в поле **CancellationHandler** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Ложь|Указывает выполняемое действие при компенсации для действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Compensate>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Компенсатионхандлер** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Ложь|Указывает действие, выполняемое при подтверждении действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Confirm>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Конфирматионхандлер** конструктора действий **CompensableActivity** . Добавьте текст подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также:

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
