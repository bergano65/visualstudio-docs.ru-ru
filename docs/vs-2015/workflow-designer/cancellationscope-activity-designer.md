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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659180"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope
Конструктор действий **CancellationScope** используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.

## <a name="the-cancellationscope-activity"></a>Действие CancellationScope
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.

### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope
 Конструктор действий **CancellationScope** можно найти в категории " **транзакция** " **панели элементов**, щелкнув вкладку " **область элементов** " (или выбрав [!INCLUDE[wfd2](../includes/wfd2-md.md)] пункт **панель инструментов** в меню **вид** или нажав клавиши CTRL + ALT + X).

 Конструктор действий **CancellationScope** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.CancellationScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **CancellationScope** или в поле **DisplayName** сетки свойств.

### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в таблице свойств, но другие свойства должны изменяться в [!INCLUDE[wfd2](../includes/wfd2-md.md)] области.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Верно|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите действие из **области элементов** в поле **текст** в конструкторе действия **CancellationScope** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Верно|Указывает действие, выполняемое в случае отмены. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите действие из **области элементов** в поле **CancellationHandler** конструктора действий **CancellationScope** с текстом подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также:
 [Транзакция](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [компенсации](../workflow-designer/compensate-activity-designer.md) [подтвердить](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)