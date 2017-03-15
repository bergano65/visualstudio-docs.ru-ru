---
title: "Метод &quot;&lt;имя_метода&gt;&quot; не имеет сигнатуры, совместимой с делегатом &quot;&lt;имя_делегата&gt;&quot; | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_метода&gt;&quot; не имеет сигнатуры, совместимой с делегатом &quot;&lt;имя_делегата&gt;&quot;
Эта ошибка возникает, когда требуется преобразование между методом и делегатом, которое невозможно. Причиной ошибки может быть преобразование между параметрами или, когда метод и делегат являются функциями, преобразование в возвращаемые значения.  
  
 Следующий код иллюстрирует неудачные преобразования. Делегат — `FunDel`.  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 Следующие функции отличаются от `FunDel` способом, который приведет к этой ошибке.  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 Каждый из следующих операторов назначения вызывает ошибку.  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **Идентификатор ошибки:** BC31143  
  
### Исправление ошибки  
  
-   Проверьте соответствующие параметры и типы возврата \(при их наличии\), чтобы определить, какая пара несовместима.  
  
## См. также  
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)