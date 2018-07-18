---
title: Конструктор рабочих процессов - ExistsInCollection&lt;T&gt; конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5625f42489752647da57fad9956cff8c64b8f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974404"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > конструктора действий

**ExistsInCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.ExistsInCollection%601> действия.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > действия
 Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.

### <a name="using-the-existsincollectiont-activity-designer"></a>С помощью ExistsInCollection\<T > конструктора действий
 **ExistsInCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **ExistsInCollection\<T >** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из ExistsInCollection < Int32\>. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.)  <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **ExistsInCollection < T\>**  конструктора или в **DisplayName** поле сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Свойства
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ExistsInCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Да|Элемент, добавляемый в коллекцию\<T >. Этот элемент относится к типу *T* относится к типу *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection < TypeArgument\>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)