---
title: "Анонимный тип должен содержать не менее одного члена | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Анонимный тип должен содержать не менее одного члена
Список инициализаторов в объявлении анонимного типа не может быть пустым.  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **Идентификатор ошибки:** BC36574  
  
### Исправление ошибки  
  
-   Объявите член в фигурных скобках, как показано в следующем коде.  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)