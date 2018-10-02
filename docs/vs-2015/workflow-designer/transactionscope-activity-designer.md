---
title: Конструктор действия TransactionScope | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ccd5aaeda7a162c88c0c82de882dfaab950595cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573107"
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope
**TransactionScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TransactionScope> действия.  
  
## <a name="the-transactionscope-activity"></a>Действие TransactionScope  
 Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope  
 **TransactionScope** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **панели элементов**  вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **TransactionScope** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **TransactionScope** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-transactionscope-properties"></a>Свойства TransactionScope  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Но другие свойства следует изменять в таблице свойств.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить <xref:System.Activities.Statements.TransactionScope.Body%2A> действие, перетащите его из **элементов** в **текст** поле на **TransactionScope** конструктора действий с текстом подсказки «перетащить действие здесь».|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Да|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|  
  
## <a name="see-also"></a>См. также  
 [Транзакции](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Компенсации](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)