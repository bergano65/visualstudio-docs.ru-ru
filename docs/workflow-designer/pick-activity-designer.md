---
title: "Конструктор действия Pick | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa06d4c63dbb18c080c8a6b8ffda01838607ba55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="pick-activity-designer"></a>Конструктор действия Pick
Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий. Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.  
  
## <a name="the-pick-activity"></a>Действие Pick  
 Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером. Таким образом [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>. В начале <xref:System.Activities.Statements.Pick> выполнения действия, все действия триггера <xref:System.Activities.Statements.PickBranch> элементов. Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора  
 **Выбрать** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав **элементов**вкладки [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Выбора** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно помещаются конструкторы, например внутри  **Последовательность** конструктора действий. После переноса в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], он создает действие <xref:System.Activities.Statements.Pick>, которое по умолчанию содержит два пустых действия <xref:System.Activities.Statements.PickBranch> в виде элементов с именами отображения Branch1 и Branch2. Соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в **PickBranch** заголовке конструктора действий или в **свойства** для каждой ветви.  
  
 Существует два способа добавления <xref:System.Activities.Statements.PickBranch> действий в коллекцию <xref:System.Activities.Statements.Pick> объектов: перетаскивание **PickBranch** конструктора из **элементов** или с помощью контекстного меню на в пределах **выбора** область конструктора. Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md) раздела. Обратите внимание, что единственный элемент, который может быть помещен внутрь **выбора** конструктор операций является **PickBranch** конструктора действий.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Свойства действия Pick в конструкторе рабочих процессов  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке. Значение по умолчанию - Pick. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## <a name="see-also"></a>См. также  
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)   
 [Действие Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Использование действия Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)