---
title: '&lt; &gt; Конструктор действий ClearCollection T | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657023"
---
# <a name="clearcollectionlttgt-activity-designer"></a>&lt; &gt; Конструктор активности ClearCollection T
Конструктор **действий \<T> ClearCollection** используется для создания и настройки <xref:System.Activities.Statements.ClearCollection%601> действия.

## <a name="the-clearcollectiont-activity"></a>Действие ClearCollection \<T>
 Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.

### <a name="using-the-clearcollectiont-activity-designer"></a>Использование \<T> конструктора действий ClearCollection
 Конструктор **действий \<T> ClearCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выбрав пункт **панель инструментов** в меню **вид** или нажав клавиши CTRL + ALT + X).

 Конструктор **действий \<T> ClearCollection** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.ClearCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> ClearCollection \<Int32> . (По умолчанию *TypeArgument* имеет значение **Int32**. Это можно изменить в сетке свойств.) <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий ** \<T> ClearCollection** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-clearcollectiont-properties"></a>Свойства ClearCollection \<T>
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>. Значение по умолчанию — ClearCollection \<Int32> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Верно|Задает коллекцию для очистки от элементов. Эта коллекция имеет тип **ICollection \<TypeArgument> .** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Верно|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|

## <a name="see-also"></a>См. также:
 [Коллекция](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)