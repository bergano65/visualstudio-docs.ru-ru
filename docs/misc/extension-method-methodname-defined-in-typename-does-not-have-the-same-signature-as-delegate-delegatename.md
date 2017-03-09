---
title: "Сигнатура метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;, отличается от сигнатуры делегата &quot;&lt;имя_делегата&gt;&quot; | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Сигнатура метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;, отличается от сигнатуры делегата &quot;&lt;имя_делегата&gt;&quot;
Существует несоответствие между сигнатурами метода расширения и делегата, который вы пытаетесь использовать. Типы параметров и значения, возвращаемые классом делегата, определяются оператором `Delegate`. Для создания экземпляра данного типа делегата можно использовать любую процедуру с соответствующими типами параметров и типами возвращаемых значений. В приведенном ниже примере ошибка возникает из\-за несоответствия сигнатуры метода расширения `Example` и сигнатуры делегата `Del`.  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **Идентификатор ошибки:** BC36580  
  
### Исправление ошибки  
  
-   Проверьте, имеют ли делегат и метод расширения одинаковое число параметров.  
  
-   Проверьте, расположены ли параметры делегата и метода в одинаковом порядке.  
  
-   Проверьте типы данных соответствующих параметров делегата и метода на их совместимость.  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)