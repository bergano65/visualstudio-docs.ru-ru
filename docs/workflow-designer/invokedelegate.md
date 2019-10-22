---
title: конструктор рабочих процессов Инвокеделегате
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650177"
---
# <a name="invokedelegate"></a>InvokeDelegate

Конструктор **инвокеделегате** используется для создания и настройки действия <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Действие Инвокеделегате

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="use-the-invokedelegate-activity-designer"></a>Использование конструктора действий Инвокеделегате

Доступ к конструктору действий **инвокеделегате** в категории **примитивы** **панели элементов**. Конструктор действий **инвокеделегате** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence>. При удалении конструктора действий создается <xref:System.Activities.Statements.InvokeDelegate> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию Инвокеделегате. @No__t_0 можно изменить в заголовке конструктора действий **инвокеделегате** или в поле **DisplayName** сетки свойств.

### <a name="the-invokedelegate-properties"></a>Свойства Инвокеделегате

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств, а некоторые можно изменить на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то, что <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, лучше использовать один из них.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство может быть изменено на поверхности конструктора и является обязательным.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключи — это имена объектов параметров в <xref:System.Activities.ActivityDelegate>, а значения — это аргументы, выражения которых вычисляются и присваиваются соответствующим объектам параметров. Чтобы отобразить диалоговое окно **DelegateArguments** , в котором можно задать это свойство, нажмите кнопку с многоточием в поле **DelegateArguments** сетки свойств. Щелкните поле **Создать аргумент** , чтобы добавить аргументы.|

## <a name="see-also"></a>См. также

- [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)