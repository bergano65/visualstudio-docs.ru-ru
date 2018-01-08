---
title: "Конструктор действия Compensate | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 7d6317299bef78b4f5ee882bcf8d1353b81b5100
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate
**Compensate** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.  
  
## <a name="the-compensate-activity"></a>Действие Compensate  
 Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.  
  
 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.  
  
### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate  
 **Compensate** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов** вкладка на левой стороне [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Compensate** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Compensate> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Compensate. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Compensate** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-compensate-properties"></a>Свойства Compensate  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], однако свойство <xref:System.Activities.Statements.Compensate.Target%2A> можно изменить только в таблице свойств.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Compensate>. Значение по умолчанию - Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Compensate>.|  
  
## <a name="see-also"></a>См. также  
 [Транзакции](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Конструктор действия Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Подтверждение](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)