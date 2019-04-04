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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61398efe1849c6038e13a68ae3b2e2f5f80f1d5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991660"
---
# <a name="invokemethod-activity-designer"></a>Конструктор действия InvokeMethod
**InvokeMethod** конструктор используется для создания и настройки <xref:System.Activities.Statements.InvokeMethod> действия.  
  
## <a name="the-invokemethod-activity"></a>Действие InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Вызывает открытый метод заданного объекта или типа.  
  
### <a name="using-the-invokemethod-activity-designer"></a>Использование конструктора операций InvokeMethod  
 **InvokeMethod** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **панелиэлементов** вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню, или же CTRL + ALT + X.)  
  
 **InvokeMethod** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности где когда-либо обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Это создает действие <xref:System.Activities.Statements.InvokeMethod> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InvokeMethod** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-invokemethod-properties"></a>Свойства InvokeMethod  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeMethod> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.InvokeMethod>. Значение по умолчанию - InvokeMethod.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Имя метода, вызываемого, когда выполняется действие. Вызываемый метод должен быть объявлен как **открытый**. Это свойство можно изменить в области конструктора. Это свойство обязательное.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Коллекция параметров вызванного метода. Параметры должны добавляться в коллекцию в том же порядке, в котором они представлены в сигнатуре метода. В сетке свойств нажмите кнопку с многоточием в **параметры** поля, он отображает **параметры** диалоговое окно, в котором можно установить это свойство. Нажмите кнопку **создать аргумент** кнопку, чтобы добавить параметры.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Возвращаемое значение вызова метода.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Указывает, вызывается ли метод асинхронно. Значение по умолчанию — **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Объект, в котором содержится метод для вызова. Это свойство можно изменить в области конструктора.<br /><br /> Необходимо указать либо <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, либо <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Тип параметра <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Это свойство можно изменить в области конструктора. Это свойство необходимо устанавливать, только если вызванный метод является статическим.|  
  
 Чтобы передать параметры в виде на языке C# **out** параметра (например, `Method1(out myParam)),` следует использовать **OutArgument** вместо **InOutArgument**  
  
 Методы с аргументами, называющиеся **TargetObject** или **результат** невозможно вызывать при помощи <xref:System.Activities.Statements.InvokeMethod> действия. Это происходит потому, что действие <xref:System.Activities.Statements.InvokeMethod> регистрирует <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> и <xref:System.Activities.Statements.InvokeMethod.Result%2A> в <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 Алгоритм регистрирования параметров в <xref:System.Activities.Activity.CacheMetadata%2A> отображается в следующем списке:  
  
1. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3. Переходите от одного пункта коллекции <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> к другому и зарегистрируйте каждый аргумент.  
  
   Результирующее исключение типа <xref:System.Activities.InvalidWorkflowException> со следующим сообщением: «InvokeMethod»: Переменная, аргумент RuntimeArgument или DelegateArgument уже существует с именем «TargetObject». Имена должны быть уникальными в среде.  
  
   Это ограничение не применяется к <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> и <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, поскольку они не являются аргументами рабочего процесса и поэтому не регистрируются в коллекции <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> действия <xref:System.Activities.Statements.InvokeMethod> в методе <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## <a name="see-also"></a>См. также  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)   
 [назначить](../workflow-designer/assign-activity-designer.md)   
 [Задержка](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)