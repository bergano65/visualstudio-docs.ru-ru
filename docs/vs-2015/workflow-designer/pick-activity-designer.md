---
title: Конструктор действия Pick | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 15320289c3f668f2bc0a84d9653110d02536a32e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694502"
---
# <a name="pick-activity-designer"></a>Конструктор действия Pick
Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий. Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.  
  
## <a name="the-pick-activity"></a>Действие Pick  
 Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером. Таким образом [!INCLUDE[wfd1](../includes/wfd1-md.md)] обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>. В начале выполнения действия <xref:System.Activities.Statements.Pick> планируются все действия триггера из всех элементов <xref:System.Activities.Statements.PickBranch>. Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора  
 **Выбрать** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав **элементов**вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Выбрать** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно помещаются конструкторы, например внутри  **Последовательность** конструктора действий. После сброса в [!INCLUDE[wfd2](../includes/wfd2-md.md)], он создает действие <xref:System.Activities.Statements.Pick>, которое по умолчанию содержит два пустых действия <xref:System.Activities.Statements.PickBranch> в виде элементов с именами отображения Branch1 и Branch2. Соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в **PickBranch** заголовке конструктора действий или в **свойства** окна для каждой ветви.  
  
 Существует два способа добавления <xref:System.Activities.Statements.PickBranch> действий в коллекцию <xref:System.Activities.Statements.Pick> объект: перетаскивания **PickBranch** конструктора из **элементов** или с помощью контекстного меню на в рамках **выбрать** область конструктора. Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md) раздела. Обратите внимание на то, что единственный элемент, который можно поместить в **выбрать** конструктор операций является **PickBranch** конструктора действий.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Свойства действия Pick в конструкторе рабочих процессов  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке. Значение по умолчанию - Pick. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## <a name="see-also"></a>См. также  
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)   
 [Действие Pick](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Использование действия Pick](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)