---
title: Конструктор действий по конструктор рабочих процессовму подбору
description: Узнайте, как действие выбора предоставляет поток управления на основе событий и выполняет одну из нескольких ветвей в ответ на событие, вызывающее срабатывание.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b616cf3d9b7eba5b2a2e9de23546a8a5f9c36ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968701"
---
# <a name="pick-activity-designer"></a>Конструктор действия Pick

Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий. Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.

## <a name="the-pick-activity"></a>Действие Pick

Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером. Таким образом конструктор рабочих процессов обеспечивает моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>. В начале <xref:System.Activities.Statements.Pick> выполнения действия запланированы все действия триггера <xref:System.Activities.Statements.PickBranch> элементов. Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.

### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора

Доступ к конструктору действий **выборки** в категории **поток управления** **панели элементов**. Конструктор операций **подбора** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются конструкторы действий, например в конструкторе действий **последовательности** . После его удаления в конструктор рабочих процессов создается <xref:System.Activities.Statements.Pick> действие, которое по умолчанию содержит два пустых <xref:System.Activities.Statements.PickBranch> действия в виде элементов с отображаемыми именами branch1 и branch2. Эти соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в заголовке конструктора действий **PickBranch** или в окне **свойств** для каждой ветви.

Существует два способа добавления <xref:System.Activities.Statements.PickBranch> действий в коллекцию <xref:System.Activities.Statements.Pick> объекта: перетаскивание конструктора **PickBranch** из **панели элементов** или с помощью контекстного меню в области конструктора **выборки** . Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Обратите внимание, что единственный элемент, который можно поместить в конструктор действия **выбора** , — это конструктор действий **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Свойства действия Pick в конструкторе рабочих процессов

В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке. Значение по умолчанию - Pick. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также раздел

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [Действие Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Использование действия Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)