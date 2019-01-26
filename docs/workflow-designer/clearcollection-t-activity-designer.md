---
title: Конструктор рабочих процессов - ClearCollection<T> конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f086acbbdbbdf442b1684cc5c32d1fa13eb785f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034068"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > конструктора действий

**ClearCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.ClearCollection%601> действия.

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > действия

Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.

### <a name="using-the-clearcollectiont-activity-designer"></a>С помощью ClearCollection\<T > конструктора действий

**ClearCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**ClearCollection\<T >** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где размещаются действия, например в <xref:System.Activities.Statements.Sequence>. Удаление конструктора действий создает <xref:System.Activities.Statements.ClearCollection%601> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из ClearCollection < Int32\>. (По умолчанию *TypeArgument* — **Int32**. TypeArgument можно изменить в сетке свойств.) <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **ClearCollection < T\>**  конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > Свойства

В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>. Значение по умолчанию — ClearCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Задает коллекцию для очистки от элементов. Эта коллекция имеет тип **ICollection\<TypeArgument >.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)