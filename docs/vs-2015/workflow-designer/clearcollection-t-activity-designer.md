---
title: Конструктор действий &gt; ClearCollection &lt;T | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657023"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Конструктор действий &gt; ClearCollection &lt;T
Конструктор действий **> ClearCollection \<T** используется для создания и настройки действия <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Действие ClearCollection \<T >
 Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.

### <a name="using-the-clearcollectiont-activity-designer"></a>Использование конструктора действий > ClearCollection \<T
 Конструктор действий **ClearCollection \<T >** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в окне Меню " **вид** " или CTRL + ALT + X.)

 Конструктор действий **ClearCollection \<T >** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)]ную поверхность, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ClearCollection%601> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию ClearCollection \<Int32 >. (По умолчанию *TypeArgument* имеет значение **Int32**. Это можно изменить в сетке свойств.) Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **ClearCollection \<T >** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-clearcollectiont-properties"></a>Свойства \<T ClearCollection >
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>. Значение по умолчанию — ClearCollection \<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Задает коллекцию для очистки от элементов. Эта коллекция имеет тип **ICollection \<TypeArgument >.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|True|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также раздел
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)