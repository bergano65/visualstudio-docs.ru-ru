---
title: "Option Strict On запрещает операнды типа Object для оператора &quot;&lt;имя_оператора&gt;&quot;. | Microsoft Docs"
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
  - "bc30038"
  - "vbc30038"
helpviewer_keywords: 
  - "BC30038"
ms.assetid: eb047d36-1fb4-460d-ae98-c76f31a89bed
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On запрещает операнды типа Object для оператора &quot;&lt;имя_оператора&gt;&quot;.
Единственными операторами, определенными для объектных переменных, являются `Is` и `TypeOf...Is`. Если `Option Strict` является `On`, все операнды должны иметь типы данных, определенные для данного оператора.  
  
 **Идентификатор ошибки:** BC30038  
  
### Исправление ошибки  
  
-   Используйте соответствующие функции преобразования типов, такие как `CInt` или `CStr`, чтобы преобразовать операнды в типы данных, определенные для оператора.  
  
## См. также  
 [Оператор Is](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Функции преобразования типов](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)