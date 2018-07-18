---
title: Конструктор рабочих процессов - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3d68fa1b777663ff8975f8ce99100d8eddc5f05d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976923"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeDelegate> действия.

## <a name="the-invokedelegate-activity"></a>Действие InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="using-the-invokedelegate-activity-designer"></a>Использование конструктора действий InvokeDelegate

**InvokeDelegate** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов** вкладки конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или же CTRL + ALT + X.)

**InvokeDelegate** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, где каждый раз, если обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Это создает действие <xref:System.Activities.Statements.InvokeDelegate> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeDelegate** конструктора или в **DisplayName** поле сетки свойств.

### <a name="the-invokedelegate-properties"></a>Свойства InvokeDelegate

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые можно изменить в области Designerdesigner рабочего процесса.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство можно изменить в области конструктора. Это свойство обязательное.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключи — это имена объектов параметров на <xref:System.Activities.ActivityDelegate> и значения, которые являются аргументами тех выражений вычисляются и назначены соответствующие объекты параметров. В сетке свойств нажмите кнопку с многоточием в **DelegateArguments** поля, он отображает **DelegateArguments** диалоговое окно, в котором можно установить это свойство. Нажмите кнопку **создать аргумент** поля для добавления аргументов.|

## <a name="see-also"></a>См. также

- [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)