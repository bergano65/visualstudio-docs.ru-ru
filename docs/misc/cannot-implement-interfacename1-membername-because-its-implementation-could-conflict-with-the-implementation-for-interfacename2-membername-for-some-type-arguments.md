---
title: "Невозможно реализовать &quot;&lt;имя_интерфейса1&gt;.&lt;имя_члена&gt;&quot;, поскольку это может привести к конфликту с реализацией &quot;&lt;имя_интерфейса2&gt;.&lt;имя_члена&gt;&quot; для некоторых аргументов типа | Microsoft Docs"
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
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно реализовать &quot;&lt;имя_интерфейса1&gt;.&lt;имя_члена&gt;&quot;, поскольку это может привести к конфликту с реализацией &quot;&lt;имя_интерфейса2&gt;.&lt;имя_члена&gt;&quot; для некоторых аргументов типа
Класс реализует более одного универсального интерфейса, один из которых наследуется от другого, и две реализации члена интерфейса могут конфликтовать из\-за определенных значений аргументов типа.  
  
 Эта ошибка может быть вызвана указанными ниже операторами.  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 Так как `iFace2` наследуется от `iFace1` с помощью собственного параметра типа \(`u`\), `testClass` будет реализовывать две версии `iFace1.testSub` с одинаковыми сигнатурами, если одинаковые аргументы типа будет переданы `y` и `z`. Это вызовет неоднозначность в том, к какой версии получать доступ.  
  
 **Идентификатор ошибки:** BC32125  
  
### Исправление ошибки  
  
-   Измените структуру наследования интерфейсов так, чтобы `iFace1` нельзя было реализовать с двумя разными аргументами типа.  
  
     \-или\-  
  
-   Удалите из оператора `Implements` один из интерфейсов, который приводит к появлению конфликта.  
  
## См. также  
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [НЕ В СБОРКЕ. ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)