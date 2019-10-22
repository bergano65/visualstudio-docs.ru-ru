---
title: Инвокеделегате | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659007"
---
# <a name="invokedelegate"></a>InvokeDelegate

Конструктор **инвокеделегате** используется для создания и настройки действия <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Действие InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="using-the-invokedelegate-activity-designer"></a>Использование конструктора действий InvokeDelegate

Конструктор действий **инвокеделегате** можно найти в категории **примитивы** **области элементов**, щелкнув вкладку **область элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в меню **вид** или CRTL + ALT + X.)

Конструктор действий **инвокеделегате** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)]ную поверхность, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence>. Это создает действие <xref:System.Activities.Statements.InvokeDelegate> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. @No__t_0 можно изменить в заголовке конструктора действий **инвокеделегате** или в поле **DisplayName** сетки свойств.

### <a name="the-invokedelegate-properties"></a>Свойства InvokeDelegate

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство можно изменить в области конструктора. Это свойство обязательное.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключи - это имена объектов <xref:System.Activities.DelegateArgument> в объекте <xref:System.Activities.ActivityDelegate> и значения, которые являются аргументами тех выражений, которые вычисляются и присваиваются соответствующим объектам <xref:System.Activities.DelegateArgument>. В сетке свойств нажмите кнопку с многоточием в поле **DelegateArguments** , чтобы отобразить диалоговое окно **DelegateArguments** , позволяющее задать это свойство. Щелкните поле **Создать аргумент** , чтобы добавить аргументы.|

## <a name="see-also"></a>См. также

- [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)