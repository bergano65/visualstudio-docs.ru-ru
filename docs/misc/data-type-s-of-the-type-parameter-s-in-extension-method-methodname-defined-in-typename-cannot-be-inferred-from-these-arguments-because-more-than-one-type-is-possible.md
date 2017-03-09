---
title: "Типы данных параметров типа в методе расширения &quot;&lt;имя_метода&gt;&quot;, которые определены в &quot;&lt;имя_типа&gt;&quot;, не могут быть выведены из этих аргументов, так как возможен более чем один тип | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36652"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы данных параметров типа в методе расширения &quot;&lt;имя_метода&gt;&quot;, которые определены в &quot;&lt;имя_типа&gt;&quot;, не могут быть выведены из этих аргументов, так как возможен более чем один тип
Типы данных параметров типа в методе расширения "\<имя\_метода\>", которые определены в "\<имя\_типа\>", не могут быть выведены из этих аргументов, так как возможен более чем один тип. Исправить эту ошибку может явное указание типов данных.  
  
 Предпринята попытка использования вывода типов для определения типа \(или типов\) параметра \(или параметров\) типа в вызове универсального метода расширения. Компилятор обнаружил несколько возможных типов данных для одного или нескольких параметров типа и сообщает об ошибке.  
  
> [!NOTE]
>  Когда аргументы являются обязательными \(например, в операторах выражений запросов\), это сообщение об ошибке отображается без второго предложения.  
  
 Эта ошибка показана в приведенном ниже коде.  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **Идентификатор ошибки:** BC36655 \(в запросах [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\) и BC36652 \(вне запросов\)  
  
### Исправление ошибки  
  
-   Если ошибка возникает за пределами запроса, попробуйте явно указать тип данных параметра \(или параметров\) типа.  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)