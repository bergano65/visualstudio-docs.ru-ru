---
title: '&lt; &gt; Конструктор действий ExistsInCollection T | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656736"
---
# <a name="existsincollectionlttgt-activity-designer"></a>&lt; &gt; Конструктор активности ExistsInCollection T
Конструктор **действий \<T> ExistsInCollection** используется для создания и настройки <xref:System.Activities.Statements.ExistsInCollection%601> действия.

## <a name="the-existsincollectiont-activity"></a>Действие ExistsInCollection \<T>
 Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.

### <a name="using-the-existsincollectiont-activity-designer"></a>Использование \<T> конструктора действий ExistsInCollection
 Конструктор **действий \<T> ExistsInCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выберите пункт **панель инструментов** в меню **вид** или нажмите клавиши CTRL + ALT + X).

 Конструктор **действий \<T> ExistsInCollection** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection \<Int32> . (По умолчанию *TypeArgument* имеет значение **Int32**. Его можно изменить в сетке свойств.)  <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий ** \<T> ExistsInCollection** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-existsincollectiont-properties"></a>Свойства ExistsInCollection \<T>
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ExistsInCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection \<Int32> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Верно|Элемент, добавляемый в коллекцию \<T> . Этот элемент относится к типу *T* типа *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Верно|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection \<TypeArgument> .** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Верно|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|Неверно|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также:
 [Коллекция](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)