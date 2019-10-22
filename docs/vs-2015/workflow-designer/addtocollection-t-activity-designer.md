---
title: Конструктор действий &gt; AddToCollection &lt;T | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659207"
---
# <a name="addtocollectionlttgt-activity-designer"></a>Конструктор действий &gt; AddToCollection &lt;T
Конструктор действий **> AddToCollection \<T** используется для создания и настройки действия <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Действие AddToCollection \<T >
 Действие <xref:System.Activities.Statements.AddToCollection%601> добавляет элемент в коллекцию.

### <a name="using-the-addtocollectiont-activity-designer"></a>Использование конструктора действий > AddToCollection \<T
 Конструктор действий **AddToCollection \<T >** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в окне Меню " **вид** " или CTRL + ALT + X.)

 Конструктор действий **AddToCollection \<T >** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)]ную поверхность, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.AddToCollection%601> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию AddToCollection \<Int32 >. (По умолчанию *TypeArgument* имеет значение **Int32**. Это можно изменить в сетке свойств.) Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **AddToCollection \<T >** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-addtocollectiont-properties"></a>Свойства \<T AddToCollection >
 В следующей таблице показаны свойства <xref:System.Activities.Statements.AddToCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.AddToCollection%601>. Значение по умолчанию — AddToCollection \<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Элемент, добавляемый в коллекцию \<T >. Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection \<TypeArgument >** . Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также раздел
 [Коллекция](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T > действия конструктор](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T](../workflow-designer/existsincollection-t-activity-designer.md) > [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)