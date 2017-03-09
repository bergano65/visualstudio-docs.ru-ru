---
title: "Модификатор, допускающий значение NULL, не может указываться в объявлениях переменной с &quot;As New&quot; | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модификатор, допускающий значение NULL, не может указываться в объявлениях переменной с &quot;As New&quot;
Модификатор типа, допускающего значение NULL, был включен в объявление переменной, в котором указано ключевое слово `As New`. Например, приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **Идентификатор ошибки:** BC33109  
  
### Исправление ошибки  
  
1.  Удалите ключевое слово `New` из объявления переменной типа, допускающего значение NULL, как показано в следующем примере:  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)