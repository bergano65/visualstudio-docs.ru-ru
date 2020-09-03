---
title: Назначить конструктор действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659190"
---
# <a name="assign-activity-designer"></a>Конструктор действий Assign
Конструктор **назначения** действий используется для создания и настройки <xref:System.Activities.Statements.Assign> действия.

## <a name="the-assign-activity"></a>Действие Assign
 Действие <xref:System.Activities.Statements.Assign> присваивает значение переменной или аргументу.

### <a name="using-the-assign-activity-designer"></a>Использование конструктора действия Assign
 Конструктор **назначения** действий можно найти в категории **примитивы** **области элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X).

 Конструктор **назначения** действий можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.Assign> действие со значением **DisplayName** по умолчанию Assign. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **назначения** или в поле **DisplayName** сетки свойств.

### <a name="the-assign-properties"></a>Свойства Assign
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Assign> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Assign>. Значение по умолчанию - Assign. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.Assign.To%2A>|Верно|Переменная или аргумент, которым присваивается <xref:System.Activities.Statements.Assign.Value%2A>. Должно быть допустимым идентификатором Visual Basic. Чтобы задать свойство, введите Visual Basic выражение в поле **Кому** в конструкторе действий **назначить** или в сетке свойств.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Верно|Значение, присваиваемое переменной. Чтобы задать <xref:System.Activities.Statements.Assign.Value%2A> , введите Visual Basic выражение в поле **значение** в конструкторе действий **назначить** или в сетке свойств.|

## <a name="see-also"></a>См. также:
 [Немедленные](../workflow-designer/delay-activity-designer.md) [примитивы](../workflow-designer/primitives-activity-designers.md) метод [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)