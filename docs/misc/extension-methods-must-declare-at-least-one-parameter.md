---
title: "В методах расширения должен быть объявлен по крайней мере один параметр | Microsoft Docs"
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
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В методах расширения должен быть объявлен по крайней мере один параметр
В методах расширения должен быть объявлен по крайней мере один параметр. Первый параметр указывает тип для расширения.  
  
 Метод расширения без параметров является недопустимым, так как первый параметр задает тип данных, который расширяет метод. Первый параметр привязан к экземпляру типа данных, который вызывает метод.  
  
 **Идентификатор ошибки:** BC36552  
  
### Исправление ошибки  
  
-   Добавьте параметр типа, который расширяет метод.  
  
## Пример  
 Первый параметр в приведенном ниже примере указывает на то, что метод `Print` расширяет тип данных `String`.  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Когда метод расширения вызывается указанным ниже образом, параметр `str` в методе привязан к `greeting`, экземпляру `String`, который вызывает метод `Print`. Компилятор использует `greeting` в качестве аргумента для метода расширения `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Параметры и аргументы процедуры](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Процедуры](/dotnet/visual-basic/programming-guide/language-features/procedures/index)