---
title: "Конструктор действия Pick | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия Pick
Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий.Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.  
  
## Действие Pick  
 Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером.Таким образом [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] обеспечивает моделирование потока управления на основе событий.Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>.В начале выполнения действия <xref:System.Activities.Statements.Pick> планируются все действия триггера из всех элементов <xref:System.Activities.Statements.PickBranch>.Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.  
  
### Использование конструктора действия подбора  
 Конструктор операций  **Pick** можно найти в категории **Поток управленияОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций  **Pick** можно перетащить из **Области элементов** и оставить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно помещаются конструкторы, например, внутри конструктора операций  **Sequence**.После переноса в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], он создает действие <xref:System.Activities.Statements.Pick>, которое по умолчанию содержит два пустых действия <xref:System.Activities.Statements.PickBranch> в виде элементов с именами отображения Branch1 и Branch2.Соответствующие значения свойства <xref:System.Activities.Statements.PickBranch.DisplayName%2A> можно изменить в заголовке конструктора действий **PickBranch** или в окне **Свойства** для каждого участка кода.  
  
 Действия <xref:System.Activities.Statements.PickBranch> можно добавить в коллекцию объекта <xref:System.Activities.Statements.Pick> двумя способами: перетащить конструктор **PickBranch** из **Области элементов** или воспользоваться контекстным меню в области конструктора **Pick**.Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md).Обратите внимание, что единственным элементом, который можно расположить внутри конструктора операций **Pick**, является конструктор операций **PickBranch**.  
  
### Свойства действия Pick в конструкторе рабочих процессов  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке.Значение по умолчанию — Pick.Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то, что значения <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## См. также  
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)   
 [Выбор действия](../Topic/Pick%20Activity.md)   
 [Использование действия Pick](../Topic/Using%20the%20Pick%20Activity.md)