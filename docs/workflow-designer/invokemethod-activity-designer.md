---
title: "Конструктор действия InvokeMethod | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия InvokeMethod
Конструктор **InvokeMethod** используется для создания и настройки действия <xref:System.Activities.Statements.InvokeMethod>.  
  
## Действие InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Вызывает открытый метод заданного объекта или типа.  
  
### Использование конструктора операций InvokeMethod  
 Конструктор операций **InvokeMethod** можно найти в категории **ПримитивыОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **InvokeMethod** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Это создает действие <xref:System.Activities.Statements.InvokeMethod> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **InvokeMethod** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства InvokeMethod  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeMethod> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.InvokeMethod>.Значение по умолчанию — InvokeMethod.<br /><br /> Несмотря на то, что значения <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Да|Имя метода, вызываемого, когда выполняется действие.Вызываемый по умолчанию метод должен быть объявлен как **public**.Это свойство можно изменить в области конструктора.Это свойство обязательное.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Нет|Коллекция параметров вызванного метода.Параметры должны быть добавлены в коллекцию в том же порядке, в котором они представлены в сигнатуре метода.В таблице свойств нажмите кнопку с многоточием в поле «**Параметры**», после чего отобразится диалоговое окно «**Параметры**», в котором можно установить это свойство.Нажмите кнопку **Создать аргумент**, чтобы добавить параметры.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Нет|Возвращаемое значение вызова метода.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Да|Указывает, вызывается ли метод асинхронно.Значение по умолчанию — **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Нет|Объект, в котором содержится метод для вызова.Это свойство можно изменить в области конструктора.<br /><br /> Необходимо указать либо <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, либо <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Нет|Тип <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.Это свойство можно изменить в области конструктора.Это свойство необходимо устанавливать, только если вызванный метод является статическим.|  
  
 Чтобы передать параметры в качестве параметра C\# **out** \(например, `Method1(out myParam)),`, необходимо использовать **OutArgument** вместо **InOutArgument**  
  
 Методы с аргументами, называющиеся **TargetObject** or **Result**, невозможно вызывать при помощи действия <xref:System.Activities.Statements.InvokeMethod>.Это происходит потому, что действие <xref:System.Activities.Statements.InvokeMethod> регистрирует <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> и <xref:System.Activities.Statements.InvokeMethod.Result%2A> в <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 Алгоритм регистрирования параметров в <xref:System.Activities.Activity.CacheMetadata%2A> отображается в следующем списке:  
  
1.  Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Переходите от одного пункта коллекции <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> к другому и зарегистрируйте каждый аргумент.  
  
 Результирующее исключение типа <xref:System.Activities.InvalidWorkflowException> со следующим сообщением: «InvokeMethod»: переменная, аргумент RuntimeArgument или DelegateArgument уже существует с именем «TargetObject».Имена должны быть уникальными в среде.  
  
 Это ограничение не применяется к <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> и <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, поскольку они не являются аргументами рабочего процесса и поэтому не регистрируются в коллекции <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> действия <xref:System.Activities.Statements.InvokeMethod> в методе <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## См. также  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)