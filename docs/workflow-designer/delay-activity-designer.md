---
title: Конструктор рабочих процессов - конструктор действия Delay
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c26bcbe535d45e81cb37138d26192271437b9fb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981575"
---
# <a name="delay-activity-designer"></a>Конструктор действия Delay

**Задержка** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Delay> действия.

## <a name="the-delay-activity"></a>Действия Delay

Действие <xref:System.Activities.Statements.Delay> откладывает выполнение рабочего процесса на указанное время.

### <a name="use-the-delay-activity-designer"></a>Использование конструктора действия Delay

**Задержка** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладке конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**Задержка** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление конструктора действий создает <xref:System.Activities.Statements.Delay> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> задержки. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **задержка** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-delay-properties"></a>Свойства Delay

В следующей таблице показаны <xref:System.Activities.Statements.Delay> свойства и показывается, как они используются в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые из них можно изменить в рабочей области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Delay>. Значение по умолчанию - Delay. Несмотря на то что <xref:System.Activities.Activity.DisplayName%2A> значение не является обязательным, рекомендуется использовать один.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Да|Период времени, на который задерживается выполнение рабочего процесса. Это свойство задается в таблице свойств. Введите литерал <xref:System.TimeSpan> в формате 00:00:00 или выражение Visual Basic для указания периода времени.|

## <a name="see-also"></a>См. также

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Конструктор действия Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)