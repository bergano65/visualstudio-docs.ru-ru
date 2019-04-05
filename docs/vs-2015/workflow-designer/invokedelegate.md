---
title: InvokeDelegate | Документация Майкрософт
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994002"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeDelegate> действия.

## <a name="the-invokedelegate-activity"></a>Действие InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.

### <a name="using-the-invokedelegate-activity-designer"></a>Использование конструктора действий InvokeDelegate

**InvokeDelegate** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **панелиэлементов** вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню, или же CTRL + ALT + X.)

**InvokeDelegate** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности где когда-либо обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Это создает действие <xref:System.Activities.Statements.InvokeDelegate> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeDelegate** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-invokedelegate-properties"></a>Свойства InvokeDelegate

В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>. Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя <xref:System.Activities.ActivityDelegate>, вызываемого, когда выполняется действие. Это свойство можно изменить в области конструктора. Это свойство обязательное.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата. Ключи - это имена объектов <xref:System.Activities.DelegateArgument> в объекте <xref:System.Activities.ActivityDelegate> и значения, которые являются аргументами тех выражений, которые вычисляются и присваиваются соответствующим объектам <xref:System.Activities.DelegateArgument>. В сетке свойств нажмите кнопку с многоточием в **DelegateArguments** поля, он отображает **DelegateArguments** диалоговое окно, в котором можно установить это свойство. Нажмите кнопку **создать аргумент** поле для добавления аргументов.|

## <a name="see-also"></a>См. также

- [Практическое руководство. Определение и использование делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)