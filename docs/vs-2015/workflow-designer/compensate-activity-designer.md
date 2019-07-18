---
title: Конструктор действия Compensate | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f643770482c2d01f3f091157e63f8e987853da5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977194"
---
# <a name="compensate-activity-designer"></a>Конструктор действия Compensate
**Compensate** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Compensate> действия.  
  
## <a name="the-compensate-activity"></a>Действие Compensate  
 Действие <xref:System.Activities.Statements.Compensate> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Compensate> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Compensate.Target%2A>.  
  
 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.  
  
### <a name="using-the-compensate-activity-designer"></a>Использование конструктора операций Compensate  
 **Compensate** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **панелиэлементов** вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Compensate** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Compensate> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Compensate. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Compensate** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-compensate-properties"></a>Свойства Compensate  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../includes/wfd2-md.md)], однако свойство <xref:System.Activities.Statements.Compensate.Target%2A> можно изменить только в таблице свойств.  
  
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