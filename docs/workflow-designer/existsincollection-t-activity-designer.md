---
title: '&lt; &gt; Конструктор активности ExistsInCollection T'
description: Узнайте, как можно использовать <T> конструктор действий ExistsInCollection в конструктор рабочих процессов для создания и настройки <T> действия ExistsInCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 971d6bd028315ae4a8b6f3a88164c97c6f95712b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961330"
---
# <a name="existsincollectiont-activity-designer"></a>Конструктор действия ExistsInCollection\<T>

Конструктор **действий \<T> ExistsInCollection** используется для создания и настройки <xref:System.Activities.Statements.ExistsInCollection%601> действия.

## <a name="the-existsincollectiont-activity"></a>Действие ExistsInCollection \<T>

Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.

### <a name="using-the-existsincollectiont-activity-designer"></a>Использование \<T> конструктора действий ExistsInCollection

Конструктор **действий \<T> ExistsInCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор **действий \<T> ExistsInCollection** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection<Int32 \> . (По умолчанию *TypeArgument* имеет значение **Int32**. Его можно изменить в сетке свойств.)  <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **ExistsInCollection<T \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-existsincollectiont-properties"></a>Свойства ExistsInCollection \<T>

В следующей таблице показаны <xref:System.Activities.Statements.ExistsInCollection%601> Свойства и описано, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection<Int32 \> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Искомый элемент в коллекции \<T> . Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Коллекция, в которой проверяется, существует ли элемент. Эта коллекция имеет тип **ICollection<TypeArgument \> .** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)