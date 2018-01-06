---
title: "Конструктор действия Persist | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 3bd0ef80e5255a828ad31ebfa2398ff6f8b1a1e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="persist-activity-designer"></a>Конструктор действия Persist
**Persist** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Persist> действия.  
  
## <a name="the-persist-activity"></a>Действие Persist  
 Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно. Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>. Если действие <xref:System.Activities.Statements.Persist> все же используется в области несохраняемости, то во время выполнения возникнет исключение.  
  
### <a name="using-the-persist-activity-designer"></a>Использование конструктора действия Persist  
 **Persist** конструктора действий можно найти в **среды выполнения** категории **элементов**, который нажав **элементов** Вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Persist** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Persist> действия по умолчанию **DisplayName** равно Persist. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **Persist** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-persist-properties"></a>Свойства Persist  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Persist>. По умолчанию используется значение Persist. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
  
## <a name="see-also"></a>См. также  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)