---
title: "Для перечислимых типов не допускается значение NULL | Microsoft Docs"
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
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для перечислимых типов не допускается значение NULL
Базовый тип, используемый для объявления перечисления, не может допускать значение NULL. Например, следующий код вызывает эту ошибку:  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **Идентификатор ошибки:** BC32129  
  
### Исправление ошибки  
  
-   Не используйте базовый тип, допускающий значение NULL, в объявлении `Enum`.  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Оператор Enum](/dotnet/visual-basic/language-reference/statements/enum-statement)