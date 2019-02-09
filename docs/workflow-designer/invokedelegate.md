---
title: Конструктор рабочих процессов - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 511d73ea2992887f31bc8750cc9ba32934bddd91
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925375"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeDelegate> действия.

## <a name="the-invokedelegate-activity"></a>Действие InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="use-the-invokedelegate-activity-designer"></a>Использование конструктора действий InvokeDelegate

Доступ **InvokeDelegate** конструктора действий в **примитивы** категории **элементов**. **InvokeDelegate** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, где каждый раз, если обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление конструктора действий создает <xref:System.Activities.Statements.InvokeDelegate> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeDelegate** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-invokedelegate-properties"></a>Свойства InvokeDelegate

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые можно изменить в поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то что <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется использовать один.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Да|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство можно изменить в области конструктора и является обязательным.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключами являются имена объектов параметров на <xref:System.Activities.ActivityDelegate>, а значения — аргументы которого выражения вычисляются и назначены соответствующие объекты параметра. Для отображения **DelegateArguments** диалоговое окно, где можно задать это свойство, нажмите кнопку с многоточием в **DelegateArguments** поле таблицы свойств. Нажмите кнопку **создать аргумент** поле для добавления аргументов.|

## <a name="see-also"></a>См. также

- [Практическое руководство. Определение и использование делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)