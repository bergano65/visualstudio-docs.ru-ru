---
title: "Тип &quot;&lt;имя_переменной&gt;&quot; не может быть получен из выражения, содержащего &quot;&lt;имя_переменной&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_переменной&gt;&quot; не может быть получен из выражения, содержащего &quot;&lt;имя_переменной&gt;&quot;
Компилятор не может получить тип данных переменной, если переменная используется в установке ее начального значения в объявлении.  
  
 Например, если параметр `Option Infer` имеет значение `On`, не компилируются следующие примеры:  
  
-   Объявления  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   Цикл `For`  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   Цикл `For Each`  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **Идентификатор ошибки:** BC30980  
  
### Исправление ошибки  
  
-   Если две переменные предназначались для ссылки на разные значения, измените имя объявляемой переменной.  
  
-   Используйте литеральное значение вместо имени переменной в начальном значении с правой стороны назначения.  
  
-   Используйте предложение `As`, чтобы указать тип объявляемой переменной.  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Оператор For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Вывод локального типа](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \- оператор](/dotnet/visual-basic/language-reference/statements/option-infer-statement)