---
title: Конструктор рабочих процессов - ExistsInCollection&lt;T&gt; конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e912c305e58b3a902089c21ed84cc2c83c4ea64
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995951"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > конструктора действий

**ExistsInCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.ExistsInCollection%601> действия.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > действия

Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.

### <a name="using-the-existsincollectiont-activity-designer"></a>С помощью ExistsInCollection\<T > конструктора действий

**ExistsInCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**ExistsInCollection\<T >** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из ExistsInCollection < Int32\>. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.)  <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **ExistsInCollection < T\>**  конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Свойства

В следующей таблице показаны <xref:System.Activities.Statements.ExistsInCollection%601> свойства и показывается, как они используются в конструкторе:

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Да|Элемент для поиска в коллекции\<T >. Этот элемент имеет тип *T*, который имеет тип *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Да|Коллекция, в которой требуется проверить, существует ли элемент. Эта коллекция имеет тип **ICollection < TypeArgument\>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)