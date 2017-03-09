---
title: "Типы данных для параметров-типов в методе расширения &quot;&lt;имя_метода&gt;&quot;, определенном в &quot;&lt;имя_типа&gt;&quot;, не могут быть определены из этих аргументов, так как они не могут быть приведены к одному типу | Microsoft Docs"
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
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36658"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы данных для параметров-типов в методе расширения &quot;&lt;имя_метода&gt;&quot;, определенном в &quot;&lt;имя_типа&gt;&quot;, не могут быть определены из этих аргументов, так как они не могут быть приведены к одному типу
Типы данных для параметров\-типов в методе расширения "\<имя\_метода\>", определенном в "\<имя\_типа\>", не могут быть определены из этих аргументов, так как они не могут быть приведены к одному типу. Явное указание типов данных может исправить эту ошибку.  
  
 Предпринята попытка использования определения типов для определения типа \(или типов\) данных параметра \(или параметров\) типа во время определения вызова для создания универсального метода расширения. Компилятору не удалось найти тип данных, соответствующий ограничениям, налагаемым всеми аргументами. Поэтому появилось сообщение об ошибке.  
  
> [!NOTE]
>  Когда аргументы являются обязательными \(например, в операторах выражений запросов\), это сообщение об ошибке отображается без второго предложения.  
  
 Эта ошибка показана в приведенном ниже коде.  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **Идентификатор ошибки:** BC36661 и BC36658  
  
### Исправление ошибки  
  
-   Попробуйте явно преобразовать один или несколько аргументов в совместимый тип, как показано в следующем коде:  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Попробуйте указать тип данных для параметра или параметров типа, в который преобразуются аргументы, как показано в следующем коде:  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Функции преобразования типов](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Явные и неявные преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)