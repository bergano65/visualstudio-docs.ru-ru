---
title: Конструктор действия InvokeMethod | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658994"
---
# <a name="invokemethod-activity-designer"></a>Конструктор действия InvokeMethod
Конструктор **InvokeMethod** используется для создания и настройки <xref:System.Activities.Statements.InvokeMethod> действия.

## <a name="the-invokemethod-activity"></a>Действие InvokeMethod
 <xref:System.Activities.Statements.InvokeMethod> Вызывает открытый метод заданного объекта или типа.

### <a name="using-the-invokemethod-activity-designer"></a>Использование конструктора операций InvokeMethod
 Конструктор действия **InvokeMethod** можно найти в категории **примитивы** **области элементов**, щелкнув вкладку **область элементов** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в меню **вид** или CRTL + ALT + X).

 Конструктор действий **InvokeMethod** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence> . Это создает действие <xref:System.Activities.Statements.InvokeMethod> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **InvokeMethod** или в поле **DisplayName** сетки свойств.

### <a name="the-invokemethod-properties"></a>Свойства InvokeMethod
 В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeMethod> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.InvokeMethod>. Значение по умолчанию - InvokeMethod.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Верно|Имя метода, вызываемого, когда выполняется действие. Вызываемый метод должен быть объявлен как **открытый**. Это свойство можно изменить в области конструктора. Это свойство обязательное.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Неверно|Коллекция параметров вызванного метода. Параметры должны добавляться в коллекцию в том же порядке, в котором они представлены в сигнатуре метода. В сетке свойств нажмите кнопку с многоточием в поле **Параметры** , чтобы отобразить диалоговое окно **Параметры** , позволяющее задать это свойство. Нажмите кнопку **Создать аргумент** , чтобы добавить параметры.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Неверно|Возвращаемое значение вызова метода.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Верно|Указывает, вызывается ли метод асинхронно. Значение по умолчанию равно **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Неверно|Объект, в котором содержится метод для вызова. Это свойство можно изменить в области конструктора.<br /><br /> Необходимо указать либо <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, либо <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Неверно|Тип параметра <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Это свойство можно изменить в области конструктора. Это свойство необходимо устанавливать, только если вызванный метод является статическим.|

 Для передачи параметров в качестве параметра **out** C# (например, `Method1(out myParam)),` следует использовать **Аргумент** of вместо **инаутаргумент**

 Методы с аргументами, именуемыми **TargetObject** или **result** , нельзя вызывать с помощью <xref:System.Activities.Statements.InvokeMethod> действия. Это происходит потому, что действие <xref:System.Activities.Statements.InvokeMethod> регистрирует <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> и <xref:System.Activities.Statements.InvokeMethod.Result%2A> в <xref:System.Activities.Activity.CacheMetadata%2A>.

 Алгоритм регистрирования параметров в <xref:System.Activities.Activity.CacheMetadata%2A> отображается в следующем списке:

1. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Переходите от одного пункта коллекции <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> к другому и зарегистрируйте каждый аргумент.

   Результирующее исключение типа <xref:System.Activities.InvalidWorkflowException> со следующим сообщением: «InvokeMethod»: переменная, аргумент RuntimeArgument или DelegateArgument уже существует с именем «TargetObject». Имена должны быть уникальными в среде.

   Это ограничение не применяется к <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> и <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, поскольку они не являются аргументами рабочего процесса и поэтому не регистрируются в коллекции <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> действия <xref:System.Activities.Statements.InvokeMethod> в методе <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>См. также:
 Задержек [назначения](../workflow-designer/assign-activity-designer.md) [Delay](../workflow-designer/delay-activity-designer.md) [примитивов](../workflow-designer/primitives-activity-designers.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)