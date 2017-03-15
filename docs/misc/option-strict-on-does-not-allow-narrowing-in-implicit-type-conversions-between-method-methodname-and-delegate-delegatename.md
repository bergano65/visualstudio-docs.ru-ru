---
title: "Option Strict On не разрешает ограничение в неявных преобразованиях типа между методом &quot;&lt;имя_метода&gt;&quot; и делегатом &quot;&lt;имя_делегата&gt;&quot;. | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On не разрешает ограничение в неявных преобразованиях типа между методом &quot;&lt;имя_метода&gt;&quot; и делегатом &quot;&lt;имя_делегата&gt;&quot;.
С "`Option Strict` on" у вас не может быть сужающего преобразования между типом данных параметра в делегате и соответствующим параметром функции или `Sub`, назначенного переменной этого типа делегата. Например, делегат функции `Del` имеет один параметр типа `Integer`, а функции `Conversion1`, `Conversion2` и `Conversion3` имеют один параметр разных числовых типов.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 Так как имеется расширяющее преобразование из `Integer` в `Integer` и в `Long`, допустимы следующие назначения.  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 Преобразование из `Integer` в `Short` является сужающим преобразованием. Таким образом, следующее присвоение недопустимо.  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 Идентификатор ошибки: BC36663  
  
### Исправление ошибки  
  
-   Измените тип данных параметра в делегате или методе, чтобы существовало необходимое расширяющее отношение.  
  
## См. также  
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Делегаты](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)