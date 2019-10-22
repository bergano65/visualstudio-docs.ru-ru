---
title: Конструктор действий конструктор рабочих процессов-ExistsInCollection &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9dc1f6a3694b6164fe4f2187fa4c6e2b42751e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650477"
---
# <a name="existsincollectiont-activity-designer"></a>Конструктор действий > ExistsInCollection \<T

Конструктор действий **> ExistsInCollection \<T** используется для создания и настройки действия <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Действие ExistsInCollection \<T >

Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.

### <a name="using-the-existsincollectiont-activity-designer"></a>Использование конструктора действий > ExistsInCollection \<T

Конструктор действий **ExistsInCollection \<T >** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** в конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** +**ALT** +**X**.

Конструктор действий **ExistsInCollection \<T >** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию ExistsInCollection < Int32 \>. (По умолчанию *TypeArgument* имеет значение **Int32**. Его можно изменить в сетке свойств.)  Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **ExistsInCollection < t \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-existsincollectiont-properties"></a>Свойства \<T ExistsInCollection >

В следующей таблице показаны свойства <xref:System.Activities.Statements.ExistsInCollection%601> и описано, как они используются в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection < Int32 \>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Искомый элемент в коллекции \<T >. Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Коллекция, в которой проверяется, существует ли элемент. Эта коллекция имеет тип **ICollection < TypeArgument \>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)