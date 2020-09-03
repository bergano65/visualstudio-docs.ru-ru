---
title: Конструктор действий с задержкой конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abfd625a248c14f646683c7b035065e6ca096f68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876116"
---
# <a name="delay-activity-designer"></a>Конструктор действия Delay

Конструктор действий с **задержкой** используется для создания и настройки <xref:System.Activities.Statements.Delay> действия.

## <a name="the-delay-activity"></a>Действие "задержка"

Действие <xref:System.Activities.Statements.Delay> откладывает выполнение рабочего процесса на указанное время.

### <a name="use-the-delay-activity-designer"></a>Использование конструктора действия "задержка"

Конструктор действия **delay** можно найти в категории **примитивы** **панели элементов**, щелкнув вкладку **область элементов** конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор действий с **задержкой** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.Delay> действие с заданной по умолчанию <xref:System.Activities.Activity.DisplayName%2A> задержкой. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **delay** или в поле **DisplayName** сетки свойств.

### <a name="the-delay-properties"></a>Свойства задержки

В следующей таблице показаны <xref:System.Activities.Statements.Delay> Свойства и описано, как они используются в конструкторе. Эти свойства можно изменить в сетке свойств, а некоторые из них можно изменить на поверхности конструктор рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Delay>. Значение по умолчанию - Delay. Хотя это <xref:System.Activities.Activity.DisplayName%2A> значение не является обязательным, рекомендуется использовать его.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Верно|Период времени, на который задерживается выполнение рабочего процесса. Это свойство задается в таблице свойств. Введите литерал <xref:System.TimeSpan> в формате 00:00:00 или выражение Visual Basic для указания периода времени.|

## <a name="see-also"></a>См. также раздел

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Конструктор действия Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)