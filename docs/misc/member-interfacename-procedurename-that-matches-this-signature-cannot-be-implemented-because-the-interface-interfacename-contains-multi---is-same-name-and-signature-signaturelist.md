---
title: "Член &quot;&lt;имя_интерфейса&gt;.&lt;имя_процедуры&gt;&quot;, соответствующий данной сигнатуре, нельзя переопределить, поскольку интерфейс &quot;&lt;имя_интерфейса&gt;&quot; содержит несколько членов с таким же именем и сигнатурой: &lt;список_сигнатур&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;имя_интерфейса&gt;.&lt;имя_процедуры&gt;&quot;, соответствующий данной сигнатуре, нельзя переопределить, поскольку интерфейс &quot;&lt;имя_интерфейса&gt;&quot; содержит несколько членов с таким же именем и сигнатурой: &lt;список_сигнатур&gt;
Процедура или свойство пытается реализовать процедуру или свойство, заданное в реализованном интерфейсе, но компилятор обнаруживает несколько версий процедуры или свойства интерфейса с одинаковым именем и сигнатурой.  
  
 Эта ошибка может возникнуть в случае сконструированного универсального типа, как показывают приведенные ниже схематические объявления.  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 Так как `implementingClass` реализует `baseInterface`, предоставляя `String` в его параметр типа `t`, обе версии `doSomething` в `baseInterface` для `implementingClass` будут иметь одинаковые сигнатуры. В результате компилятор не может определить версию для реализации.  
  
 **Идентификатор ошибки:** BC30937  
  
### Исправление ошибки  
  
-   Измените аргумент или аргументы типа, передаваемые в базовый класс, чтобы в результате не получалось несколько одинаковых сигнатур процедур или свойств членов.  
  
     \-или\-  
  
-   Не реализуйте этот базовый класс. Его невозможно реализовать с набором аргументов типа, который вы используете, поскольку необходимо реализовать каждый из его членов.  
  
## См. также  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [НЕ В СБОРКЕ. Ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)