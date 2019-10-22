---
title: Конструктор выбора действия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672596"
---
# <a name="pick-activity-designer"></a>Конструктор действия Pick
Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий. Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.

## <a name="the-pick-activity"></a>Действие Pick
 Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером. Таким образом [!INCLUDE[wfd1](../includes/wfd1-md.md)] обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>. В начале выполнения действия <xref:System.Activities.Statements.Pick> планируются все действия триггера из всех элементов <xref:System.Activities.Statements.PickBranch>. Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.

### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора
 Конструктор операции **подбора** можно найти в категории **поток управления** **панели элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в меню **вид** или CTRL + ALT. + X)

 Конструктор операций **подбора** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)]ную поверхность, где обычно размещаются конструкторы действий, например в конструкторе действий **последовательности** . После сброса в [!INCLUDE[wfd2](../includes/wfd2-md.md)], он создает действие <xref:System.Activities.Statements.Pick>, которое по умолчанию содержит два пустых действия <xref:System.Activities.Statements.PickBranch> в виде элементов с именами отображения Branch1 и Branch2. Эти соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в заголовке конструктора действий **PickBranch** или в окне **свойств** для каждой ветви.

 Существует два способа добавления <xref:System.Activities.Statements.PickBranch> действий в коллекцию <xref:System.Activities.Statements.Pick> объекта: перетаскивание конструктора **PickBranch** из **панели элементов** или с помощью контекстного меню в области конструктора **выбора** . Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Обратите внимание, что единственный элемент, который можно поместить в конструктор действия **выбора** , — это конструктор действий **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Свойства действия Pick в конструкторе рабочих процессов
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке. Значение по умолчанию - Pick. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также раздел
 [Действие выбора](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [потока управления](../workflow-designer/control-flow-activity-designers.md) [с помощью действия "выбрать"](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)