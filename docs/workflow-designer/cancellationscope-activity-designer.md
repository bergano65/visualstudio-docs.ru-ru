---
title: "Конструктор действия CancellationScope | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c6e9206eff3eaaeb3b5a79bb8457738c21af05c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope
**CancellationScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.  
  
## <a name="the-cancellationscope-activity"></a>Действие CancellationScope  
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope  
 **CancellationScope** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов**  вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **CancellationScope** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.CancellationScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **CancellationScope** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в таблице свойств, но другие свойства должны изменяться в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] области.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите действие из **элементов** в **текст** поле на **CancellationScope** конструктора действий с текстом подсказки «Drop Действие сюда».|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Да|Указывает действие, выполняемое в случае отмены. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите действие из **элементов** в **CancellationHandler** поле на **CancellationScope** конструктора действий с подсказкой текст «Перетащить действие сюда».|  
  
## <a name="see-also"></a>См. также  
 [Транзакции](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Компенсации](../workflow-designer/compensate-activity-designer.md)   
 [Подтверждение](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)