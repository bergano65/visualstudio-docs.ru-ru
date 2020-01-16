---
title: Конструктор действий конструктор рабочих процессов-AddToCollection<T>
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115329"
---
# <a name="addtocollectiont-activity-designer"></a>Конструктор действий AddToCollection\<T >

Конструктор действий **AddToCollection\<t >** используется для создания и настройки действия <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Действие AddToCollection\<T >

Действие <xref:System.Activities.Statements.AddToCollection%601> добавляет элемент в коллекцию.

### <a name="using-the-addtocollectiont-activity-designer"></a>Использование конструктора действий AddToCollection\<T >

Конструктор действий **AddToCollection\<t >** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL**+**ALT**+**X**.

Конструктор действий **AddToCollection\<t >** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где бы находились действия, например внутри <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий **AddToCollection\<t >** создается действие <xref:System.Activities.Statements.AddToCollection%601> с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию <\>Int32 AddToCollection. (По умолчанию *TypeArgument* имеет значение **Int32**. TypeArgument можно изменить в сетке свойств.) Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **AddToCollection < t\>** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-addtocollectiont-properties"></a>Свойства AddToCollection\<T >

В следующей таблице показаны свойства <xref:System.Activities.Statements.AddToCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ложь|Понятное имя действия <xref:System.Activities.Statements.AddToCollection%601>. Значение по умолчанию — AddToCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Да|Элемент, добавляемый в коллекцию\<T >. Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Да|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection < TypeArgument\>**. Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также:

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Конструктор действий AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
