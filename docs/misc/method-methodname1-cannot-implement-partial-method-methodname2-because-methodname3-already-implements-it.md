---
title: "Метод &quot;&lt;имя_метода1&gt;&quot; не может реализовывать разделяемый метод &quot;&lt; имя_метода2&gt;&quot;, поскольку его уже реализует &quot;&lt;имя_метода3&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_метода1&gt;&quot; не может реализовывать разделяемый метод &quot;&lt; имя_метода2&gt;&quot;, поскольку его уже реализует &quot;&lt;имя_метода3&gt;&quot;
Метод "\<имя\_метода1\>" не может реализовывать разделяемый метод "\< имя\_метода2\>", поскольку его уже реализует "\<имя\_метода3\>". Только один метод может реализовывать разделяемый метод.  
  
 Нельзя иметь два разделяемых метода, реализующих одно и то же объявление разделяемого метода. Следующий код вызывает эту ошибку.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **Идентификатор ошибки:** BC31434  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)