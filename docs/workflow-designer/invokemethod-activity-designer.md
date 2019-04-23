---
title: Конструктор рабочих процессов - конструктор действия InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed5d81cce05b316ef7593639e868936e7f2fa69
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039257"
---
# <a name="invokemethod-activity-designer"></a>Конструктор действия InvokeMethod

**InvokeMethod** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeMethod> действия.

## <a name="the-invokemethod-activity"></a>Действия InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Вызывает открытый метод заданного объекта или типа.

### <a name="use-the-invokemethod-activity-designer"></a>Использование конструктора операций InvokeMethod

Доступ **InvokeMethod** конструктора действий в **примитивы** категории **элементов**. **InvokeMethod** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, где каждый раз, если обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление конструктора действий создает <xref:System.Activities.Statements.InvokeMethod> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeMethod** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-invokemethod-properties"></a>Свойства InvokeMethod

В следующей таблице показаны <xref:System.Activities.Statements.InvokeMethod> свойства и показывается, как они используются в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые можно изменить в поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeMethod>. Значение по умолчанию - InvokeMethod.<br /><br /> Несмотря на то что <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется использовать один.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Имя метода, вызываемого, когда выполняется действие. Вызываемый метод должен быть объявлен как **открытый**. Это свойство можно изменить в области конструктора и является обязательным.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Коллекция параметров вызванного метода. Параметры должны добавляться в коллекцию в том же порядке, в котором они представлены в сигнатуре метода. Для отображения **параметры** диалоговое окно, где можно задать это свойство, нажмите кнопку с многоточием в **параметры** поле таблицы свойств. Нажмите кнопку **создать аргумент** кнопку, чтобы добавить параметры.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Возвращаемое значение вызова метода.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Указывает, вызывается ли метод асинхронно. Значение по умолчанию — **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Объект, в котором содержится метод для вызова. Это свойство можно изменить в области конструктора.<br /><br /> Необходимо указать либо <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, либо <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Тип параметра <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Это свойство можно изменить в области конструктора. Это свойство необходимо устанавливать, только если вызванный метод является статическим.|

Для передачи параметров, как в C# **out** параметра (например, `Method1(out myParam))`, использовать **OutArgument** вместо **InOutArgument**

Методы с аргументами, называющиеся **TargetObject** или **результат** невозможно вызывать при помощи <xref:System.Activities.Statements.InvokeMethod> действия. Это происходит потому, что действие <xref:System.Activities.Statements.InvokeMethod> регистрирует <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> и <xref:System.Activities.Statements.InvokeMethod.Result%2A> в <xref:System.Activities.Activity.CacheMetadata%2A>.

Алгоритм регистрирования параметров в <xref:System.Activities.Activity.CacheMetadata%2A> отображается в следующем списке:

1. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Переходите от одного пункта коллекции <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> к другому и зарегистрируйте каждый аргумент.

Результирующее исключение типа <xref:System.Activities.InvalidWorkflowException> со следующим сообщением: «InvokeMethod»: Переменная, аргумент RuntimeArgument или DelegateArgument уже существует с именем «TargetObject». Имена должны быть уникальными в среде.

Это ограничение не применяется к <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> и <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Они не аргументы рабочего процесса и поэтому не регистрируются в <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> коллекцию <xref:System.Activities.Statements.InvokeMethod> действия в <xref:System.Activities.Activity.CacheMetadata%2A> метод.

## <a name="see-also"></a>См. также

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)