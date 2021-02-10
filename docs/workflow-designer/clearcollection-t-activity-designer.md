---
title: Конструктор действий конструктор рабочих процессов-ClearCollection &lt; T &gt;
description: Узнайте, как можно использовать <T> конструктор действий ClearCollection для создания и настройки <T> действия ClearCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31d576712804a75fdca57374ce82a53ff0d1ce84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942091"
---
# <a name="clearcollectiont-activity-designer"></a>Конструктор действия ClearCollection\<T>

Конструктор **действий \<T> ClearCollection** используется для создания и настройки <xref:System.Activities.Statements.ClearCollection%601> действия.

## <a name="the-clearcollectiont-activity"></a>Действие ClearCollection \<T>

Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.

### <a name="using-the-clearcollectiont-activity-designer"></a>Использование \<T> конструктора действий ClearCollection

Конструктор **действий \<T> ClearCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор **действий \<T> ClearCollection** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где бы они ни находились, где бы ни находились действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.ClearCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> ClearCollection<Int32 \> . (По умолчанию *TypeArgument* имеет значение **Int32**. TypeArgument можно изменить в сетке свойств.) <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **ClearCollection<T \>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-clearcollectiont-properties"></a>Свойства ClearCollection \<T>

В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>. Значение по умолчанию — ClearCollection<Int32 \> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Задает коллекцию для очистки от элементов. Эта коллекция имеет тип **ICollection \<TypeArgument> .** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)