---
title: '&lt; &gt; Конструктор активности AddToCollection T'
description: Сведения о том, как <T> конструктор действий AddToCollection используется для создания и настройки <T> действия AddToCollection в конструктор рабочих процессов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18811199cce88c5d57332ced99763b4f6233da8d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920185"
---
# <a name="addtocollectiont-activity-designer"></a>Конструктор действия AddToCollection\<T>

Конструктор **действий \<T> AddToCollection** используется для создания и настройки <xref:System.Activities.Statements.AddToCollection%601> действия.

## <a name="the-addtocollectiont-activity"></a>Действие AddToCollection \<T>

Действие <xref:System.Activities.Statements.AddToCollection%601> добавляет элемент в коллекцию.

### <a name="using-the-addtocollectiont-activity-designer"></a>Использование \<T> конструктора действий AddToCollection

Конструктор **действий \<T> AddToCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор **действий \<T> AddToCollection** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где бы они ни находились, где бы ни находились действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий **AddToCollection \<T>** создается <xref:System.Activities.Statements.AddToCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 \> . (По умолчанию *TypeArgument* имеет значение **Int32**. TypeArgument можно изменить в сетке свойств.) <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **AddToCollection<T \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-addtocollectiont-properties"></a>Свойства AddToCollection \<T>

В следующей таблице показаны свойства <xref:System.Activities.Statements.AddToCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.AddToCollection%601>. Значение по умолчанию — AddToCollection<Int32 \> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Элемент, добавляемый в коллекцию \<T> . Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection<TypeArgument \>**. Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Конструктор действия AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
