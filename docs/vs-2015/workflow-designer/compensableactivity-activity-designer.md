---
title: Конструктор действия CompensableActivity | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f11743e0027866fd45687f716f1989e98020c68e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977281"
---
# <a name="compensableactivity-activity-designer"></a>Конструктор действия CompensableActivity
**CompensableActivity** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.CompensableActivity> действия.  
  
## <a name="the-compensableactivity-activity"></a>Действие CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> определяет единицу работы, которая может быть подтверждена или компенсирована после успешного завершения.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Использование конструктора действия CompensableActivity  
 **CompensableActivity** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **панели элементов**  вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **CompensableActivity** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом будет создано действие <xref:System.Activities.Statements.CompensableActivity>, где имя <xref:System.Activities.Activity.DisplayName%2A> действия CompensableActivity будет иметь значение по умолчанию. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **CompensableActivity** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-compensableactivity-properties"></a>Свойства CompensableActivity  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CompensableActivity> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Activity%601.Result%2A> можно изменить в таблице свойств, но другие свойства необходимо изменять в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.CompensableActivity>. Значение по умолчанию - CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Указывает возвращаемое значение <xref:System.Activities.Statements.CompensableActivity>. Это свойство необходимо изменять в таблице свойств.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Указывает действие, для которого производится компенсация, отмена и логика подтверждения. Чтобы добавить <xref:System.Activities.Statements.CompensableActivity.Body%2A> действие, перетащите его из **элементов** в **текст** поле на **CompensableActivity** конструктора действий с текстом подсказки «удалить Действие сюда».|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Указывает действие, выполняемое в случае отмены. Чтобы добавить действие, перетащите его конструктор из **элементов** в **CancellationHandler** поле **CompensableActivity** конструктора действий с текстом подсказки «удалить Действие сюда».|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Указывает выполняемое действие при компенсации для действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Compensate>.<br /><br /> Чтобы добавить действие, перетащите его конструктор из **элементов** в **CompensationHandler** поле **CompensableActivity** конструктора действий с текстом подсказки» Перетащить действие сюда».|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Указывает действие, выполняемое при подтверждении действия <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Этот обработчик можно вызвать явным образом при помощи действия <xref:System.Activities.Statements.Confirm>.<br /><br /> Чтобы добавить действие, перетащите его конструктор из **элементов** в **ConfirmationHandler** поле **CompensableActivity** конструктора действий с текстом подсказки» Перетащить действие сюда».|  
  
## <a name="see-also"></a>См. также  
 [Транзакции](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Компенсации](../workflow-designer/compensate-activity-designer.md)   
 [Подтверждение](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)