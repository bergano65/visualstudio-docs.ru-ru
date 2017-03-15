---
title: "&quot;Option Strict On&quot; не разрешает ограничение в неявных преобразованиях типа между лямбда-выражением и делегатом &quot;&lt;имя_делегата&gt;&quot;. | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; не разрешает ограничение в неявных преобразованиях типа между лямбда-выражением и делегатом &quot;&lt;имя_делегата&gt;&quot;.
С "`Option Strict` on" у вас не может иметься сужающее преобразование между типом данных параметра в делегате и соответствующим параметром лямбда\-выражения, назначенным переменной этого типа делегата. Например, в следующем коде делегат `Del` имеет один параметр типа `Integer`.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 Таким образом, соответствующий параметр любого лямбда\-выражения, назначенный переменной типа `Del`, может быть `Integer` или любого типа данных, для которого имеется расширяющее преобразование из `Integer`.  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **Идентификатор ошибки:** BC36662  
  
### Исправление ошибки  
  
-   Измените тип данных параметра в делегате или лямбда\-выражении, чтобы существовало необходимое расширяющее отношение.  
  
-   Не указывайте типы данных параметров в лямбда\-выражении. Типы будут выводиться из соответствующих параметров в делегате.  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## См. также  
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Делегаты](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)