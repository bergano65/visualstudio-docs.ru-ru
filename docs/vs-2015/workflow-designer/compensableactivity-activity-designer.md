---
title: Конструктор действий CompensableActivity | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656992"
---
# <a name="compensableactivity-activity-designer"></a>Конструктор действия CompensableActivity
Конструктор действий **CompensableActivity** используется для создания и настройки действия <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Действие CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> определяет единицу работы, которая может быть подтверждена или компенсирована после успешного завершения.

### <a name="using-the-compensableactivity-activity-designer"></a>Использование конструктора действия CompensableActivity
 Конструктор действий **CompensableActivity** можно найти в категории " **транзакция** " **панели элементов**, щелкнув вкладку " **область элементов** " в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** ). в меню **вид** или нажмите клавиши CTRL + ALT + X.)

 Конструктор действий **CompensableActivity** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)], где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом будет создано действие <xref:System.Activities.Statements.CompensableActivity>, где имя <xref:System.Activities.Activity.DisplayName%2A> действия CompensableActivity будет иметь значение по умолчанию. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **CompensableActivity** или в поле **DisplayName** сетки свойств.

### <a name="the-compensableactivity-properties"></a>Свойства CompensableActivity
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CompensableActivity> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Activity%601.Result%2A> можно изменить в таблице свойств, но другие свойства необходимо изменять в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CompensableActivity>. Значение по умолчанию - CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Указывает возвращаемое значение <xref:System.Activities.Statements.CompensableActivity>. Это свойство необходимо изменять в таблице свойств.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Указывает действие, для которого производится компенсация, отмена и логика подтверждения. Чтобы добавить действие <xref:System.Activities.Statements.CompensableActivity.Body%2A>, перетащите действие из **области элементов** в поле **текст** в конструкторе действия **CompensableActivity** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Указывает действие, выполняемое в случае отмены. Чтобы добавить действие, перетащите его конструктор из **области элементов** в поле **CancellationHandler** конструктора действий **CompensableActivity** с текстом подсказки "перетащите действие здесь".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Указывает выполняемое действие при компенсации для действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Compensate>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Компенсатионхандлер** конструктора действий **CompensableActivity** с текстом подсказки "перетащите действие здесь".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Указывает действие, выполняемое при подтверждении действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Confirm>.<br /><br /> Чтобы добавить действие, перетащите его конструктор действий из **области элементов** в поле **Конфирматионхандлер** конструктора действий **CompensableActivity** с текстом подсказки "перетащите действие здесь".|

## <a name="see-also"></a>См. также раздел
 [Транзакция](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [компенсации](../workflow-designer/compensate-activity-designer.md) [подтвердить](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)