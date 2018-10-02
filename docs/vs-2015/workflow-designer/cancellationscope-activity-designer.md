---
title: Конструктор действия CancellationScope | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f8ddd5472a0e6540f8593c20e7f7d5735384f8e6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558454"
---
# <a name="cancellationscope-activity-designer"></a>Конструктор действия CancellationScope
**CancellationScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CancellationScope> действия.  
  
## <a name="the-cancellationscope-activity"></a>Действие CancellationScope  
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Использование конструктора операций CancellationScope  
 **CancellationScope** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **панели элементов**  вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **CancellationScope** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.CancellationScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **CancellationScope** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-cancellationscope-properties"></a>Свойства CancellationScope  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в таблице свойств, но другие свойства должны изменяться в [!INCLUDE[wfd2](../includes/wfd2-md.md)] области.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию - CancellationScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Указывает действие, для которого предусмотрена отменяющая логика. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.Body%2A> действие, перетащите его из **элементов** в **текст** поле на **CancellationScope** конструктора действий с текстом подсказки «удалить Действие сюда».|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Да|Указывает действие, выполняемое в случае отмены. Чтобы добавить <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> действие, перетащите его из **элементов** в **CancellationHandler** поле **CancellationScope** конструктора действий с указанием текст «Перетащить действие сюда».|  
  
## <a name="see-also"></a>См. также  
 [Транзакции](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Компенсации](../workflow-designer/compensate-activity-designer.md)   
 [Подтверждение](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)