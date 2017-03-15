---
title: "Члены структуры, не являющиеся общими, не могут быть объявлены как &quot;New&quot; | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Члены структуры, не являющиеся общими, не могут быть объявлены как &quot;New&quot;
Не являющаяся общей переменная в структуре объявлена с использованием предложения `New`.  
  
 Вы можете инициализировать общую ссылочную переменную в структуре, и можете иметь не являющуюся общей ссылочную переменную без инициализации, как показано в следующих строках кода.  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 Однако вы не можете инициализировать не являющуюся общей ссылочную переменную в структуре. Следующий код является неправильным.  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **Идентификатор ошибки:** BC30795  
  
### Исправление ошибки  
  
-   Удалите из объявления ссылочной переменной либо модификатор `Shared`, либо ключевое слово `New`.  
  
## См. также  
 [Оператор Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)