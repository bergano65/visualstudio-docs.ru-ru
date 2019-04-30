---
title: Конструктор рабочих процессов - конструктор действия WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dd6e3c617749d82533d8bccb7f0caaa073ac26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838624"
---
# <a name="writeline-activity-designer"></a>Конструктор действия WriteLine

**WriteLine** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.WriteLine> действия.

## <a name="the-writeline-activity"></a>Операция WriteLine

Операция <xref:System.Activities.Statements.WriteLine> выполняет запись текста в указанный объект <xref:System.IO.TextWriter>. Если не указано <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> выполняет запись текста к консоли.

### <a name="using-the-writeline-activity-designer"></a>Использование конструктора действий WriteLine

Доступ **WriteLine** конструктора действий в **примитивы** категории **элементов**. **WriteLine** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.WriteLine> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **WriteLine** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-writeline-properties"></a>Свойства WriteLine

В следующей таблице показаны свойства <xref:System.Activities.Statements.WriteLine> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые из них можно изменить на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.WriteLine>. Значение по умолчанию WriteLine. Для значения <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего всегда использовать такое значение.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Текст для записи. Чтобы задать свойство, введите выражение Visual Basic в **текст** поле **WriteLine** действие конструктора или в сетке свойств.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Класс <xref:System.IO.TextWriter>, в который <xref:System.Activities.Statements.WriteLine> записывает <xref:System.Activities.Statements.WriteLine.Text%2A>. По умолчанию - консоль.|

## <a name="see-also"></a>См. также

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)