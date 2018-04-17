---
title: AddToCollection&lt;T&gt; конструктора | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c961c8ab893b1d8b4a2d519d8b9dce27fd6f93c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; конструктора действий
**AddToCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.AddToCollection%601> действия.

## <a name="the-addtocollectiont-activity"></a>AddToCollection < T\> действия
 Действие <xref:System.Activities.Statements.AddToCollection%601> добавляет элемент в коллекцию.

### <a name="using-the-addtocollectiont-activity-designer"></a>С помощью AddToCollection\<T > конструктора действий
 **AddToCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **AddToCollection\<T >** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.AddToCollection%601> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из AddToCollection < Int32\>. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.) <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **AddToCollection < T\>**  конструктора или в **DisplayName** поле сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-addtocollectiont-properties"></a>AddToCollection < T\> свойства
 В следующей таблице показаны свойства <xref:System.Activities.Statements.AddToCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.AddToCollection%601>. Значение по умолчанию — AddToCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Да|Элемент, добавляемый в коллекцию\<T >. Этот элемент относится к типу *T*, который относится к типу *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection < TypeArgument\>**. Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > конструктора действий](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)