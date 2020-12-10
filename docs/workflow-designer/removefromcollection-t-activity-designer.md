---
title: '&lt; &gt; Конструктор активности RemoveFromCollection T'
description: В конструктор рабочих процессов Узнайте, как использовать <T> конструктор действий RemoveFromCollection для создания и настройки <T> действия RemoveFromCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 069640dccf185f2f2c738efdde6a2311352a04b6
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996101"
---
# <a name="removefromcollectiont-activity-designer"></a>Конструктор действия RemoveFromCollection\<T>

Конструктор **действий \<T> RemoveFromCollection** используется для создания и настройки <xref:System.Activities.Statements.RemoveFromCollection%601> действия.

## <a name="the-removefromcollectiontactivity"></a>Действие RemoveFromCollection \<T>

Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Использование \<T> конструктора действий RemoveFromCollection

Доступ к конструктору действий **RemoveFromCollection \<T>** в категории **коллекция** **панели элементов**.
Конструктор **действий \<T> RemoveFromCollection** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.RemoveFromCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection<Int32 \> . <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **RemoveFromCollection<T \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-removefromcollectiont-properties"></a>Свойства RemoveFromCollection<T \>

В следующей таблице показаны <xref:System.Activities.Statements.RemoveFromCollection%601> Свойства и описано, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>. Значение по умолчанию — RemoveFromCollection<Int32 \> .<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Элемент, который необходимо удалить из **коллекции \<T>**. Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Коллекция, из которой должен быть удален элемент. Эта коллекция имеет тип **ICollection<TypeArgument \> .** Чтобы указать коллекцию, введите Visual Basic выражение в сетке свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|Неверно|Значение, которое указывает, удален ли из коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)