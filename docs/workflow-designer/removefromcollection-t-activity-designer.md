---
title: Конструктор действий конструктор рабочих процессов-RemoveFromCollection &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650002"
---
# <a name="removefromcollectiont-activity-designer"></a>Конструктор действий > RemoveFromCollection \<T

Конструктор действий **> RemoveFromCollection \<T** используется для создания и настройки действия <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiontactivity"></a>Действие RemoveFromCollection \<T >

Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Использование конструктора действий > RemoveFromCollection \<T

Доступ к конструктору действий **RemoveFromCollection \<T >** в категории **коллекция** **панели элементов**.
Конструктор действий **RemoveFromCollection \<T >** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.RemoveFromCollection%601> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию RemoveFromCollection < Int32 \>. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **RemoveFromCollection < t \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-removefromcollectiont-properties"></a>Свойства RemoveFromCollection < T \>

В следующей таблице показаны свойства <xref:System.Activities.Statements.RemoveFromCollection%601> и описано, как они используются в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>. Значение по умолчанию — RemoveFromCollection < Int32 \>.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Элемент, который необходимо удалить из **коллекции \<T >** . Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Коллекция, из которой должен быть удален элемент. Эта коллекция имеет тип **ICollection < TypeArgument \>.** Чтобы указать коллекцию, введите Visual Basic выражение в сетке свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, удален ли из коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)