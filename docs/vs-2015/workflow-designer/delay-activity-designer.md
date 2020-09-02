---
title: Конструктор действий Delay | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656800"
---
# <a name="delay-activity-designer"></a>Конструктор действия Delay
Конструктор действий с **задержкой** используется для создания и настройки <xref:System.Activities.Statements.Delay> действия.

## <a name="the-delay-activity"></a>Действие Delay
 Действие <xref:System.Activities.Statements.Delay> откладывает выполнение рабочего процесса на указанное время.

### <a name="using-the-delay-activity-designer"></a>Использование конструктора действия Delay
 Конструктор действий с **задержкой** можно найти в категории **примитивы** **области элементов**, щелкнув вкладку **область элементов** (или выбрав [!INCLUDE[wfd2](../includes/wfd2-md.md)] пункт **панель инструментов** в меню **вид** или нажав клавиши CTRL + ALT + X).

 Конструктор действий с **задержкой** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.Delay>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Delay. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **delay** или в поле **DisplayName** сетки свойств.

### <a name="the-delay-properties"></a>Свойства Delay
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Delay> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Delay>. Значение по умолчанию - Delay. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Верно|Период времени, на который задерживается выполнение рабочего процесса. Это свойство задается в таблице свойств. Введите литерал <xref:System.TimeSpan> в формате 00:00:00 или выражение Visual Basic для указания периода времени.|

## <a name="see-also"></a>См. также:
 [Примитивы](../workflow-designer/primitives-activity-designers.md) [назначение](../workflow-designer/assign-activity-designer.md) [задержки конструктор действия](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)