---
title: "InvokeDelegate | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 56b132403d51a591a8832c1417bec73bde442266
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="invokedelegate"></a>InvokeDelegate
**InvokeDelegate** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeDelegate> действия.  
  
## <a name="the-invokedelegate-activity"></a>Действие InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.  
  
### <a name="using-the-invokedelegate-activity-designer"></a>Использование конструктора действий InvokeDelegate  
 **InvokeDelegate** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов** вкладка [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или же CTRL + ALT + X.)  
  
 **InvokeDelegate** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности где-либо обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Это создает действие <xref:System.Activities.Statements.InvokeDelegate> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeDelegate** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-invokedelegate-properties"></a>Свойства InvokeDelegate  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство можно изменить в области конструктора. Это свойство обязательное.|  
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключи — это имена объектов параметров на <xref:System.Activities.ActivityDelegate> и значения, которые являются аргументами тех выражений вычисляются и назначены соответствующие объекты параметров. В сетке свойств нажмите кнопку с многоточием в **DelegateArguments** поля, он отображает **DelegateArguments** диалоговое окно, в котором можно установить это свойство. Нажмите кнопку **создать аргумент** поля для добавления аргументов.|  
  
## <a name="see-also"></a>См. также  
 [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)