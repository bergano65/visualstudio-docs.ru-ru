---
title: конструктор рабочих процессов Инвокеделегате
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876077"
---
# <a name="invokedelegate"></a>InvokeDelegate

Конструктор **инвокеделегате** используется для создания и настройки <xref:System.Activities.Statements.InvokeDelegate> действия.

## <a name="the-invokedelegate-activity"></a>Действие Инвокеделегате

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="use-the-invokedelegate-activity-designer"></a>Использование конструктора действий Инвокеделегате

Доступ к конструктору действий **инвокеделегате** в категории **примитивы** **панели элементов**. Конструктор действий **инвокеделегате** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.InvokeDelegate> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> инвокеделегате. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **инвокеделегате** или в поле **DisplayName** сетки свойств.

### <a name="the-invokedelegate-properties"></a>Свойства Инвокеделегате

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств, а некоторые можно изменить на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Хотя <xref:System.Activities.Activity.DisplayName%2A> использование не является строго обязательным, лучше использовать его.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Да|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство может быть изменено на поверхности конструктора и является обязательным.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Неверно|Коллекция аргументов вызванного делегата. Ключи — это имена объектов параметров в <xref:System.Activities.ActivityDelegate> , а значения — это аргументы, выражения которых вычисляются и присваиваются соответствующим объектам параметров. Чтобы отобразить диалоговое окно **DelegateArguments** , в котором можно задать это свойство, нажмите кнопку с многоточием в поле **DelegateArguments** сетки свойств. Щелкните поле **Создать аргумент** , чтобы добавить аргументы.|

## <a name="see-also"></a>См. также раздел

- [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)