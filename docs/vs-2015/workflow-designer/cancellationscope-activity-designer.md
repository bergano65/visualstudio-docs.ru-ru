---
title: Конструктор действий CancellationScope | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659180"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope
Конструктор действий **CancellationScope** используется для создания и настройки действия <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope
 Конструктор действий **CancellationScope** можно найти в категории " **транзакция** " **области элементов**, щелкнув вкладку " **область элементов** " [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** из **представления.** меню или CTRL + ALT + X.)

 Конструктор действий **CancellationScope** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)], где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.CancellationScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **CancellationScope** или в поле **DisplayName** сетки свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в таблице свойств, но другие свойства должны изменяться в [!INCLUDE[wfd2](../includes/wfd2-md.md)] области.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.Body%2A>, перетащите действие из **области элементов** в поле **текст** в конструкторе действия **CancellationScope** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Указывает действие, выполняемое в случае отмены. Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, перетащите действие из **области элементов** в поле **CancellationHandler** в конструкторе действия **CancellationScope** с текстом подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также раздел
 [Транзакция](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [компенсации](../workflow-designer/compensate-activity-designer.md) [подтвердить](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)