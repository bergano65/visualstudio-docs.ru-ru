---
title: "Недопустимое использование Implements в объявлении оператора | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимое использование Implements в объявлении оператора
Оператор [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) задает ключевое слово [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Только процедура, свойство или событие `Function` или `Sub` может реализовывать член интерфейса. Дополнительные сведения о реализации см. в разделе [НЕ В СБОРКЕ. Примеры реализации интерфейсов в Visual Basic](http://msdn.microsoft.com/ru-ru/50bf2a30-73b6-4126-a921-075fd6eec278).  
  
 В процедуре `Operator` требуются оба ключевых слова `Public` и `Shared`, а для оператора преобразования требуется ключевое слово `Widening` или `Narrowing`. Для получения дополнительной информации см. [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **Идентификатор ошибки:** BC33004  
  
### Исправление ошибки  
  
-   Если требуется, чтобы эта процедура реализовывала член интерфейса, перепишите ее как процедуру, свойство или событие `Function` или `Sub`.  
  
-   Если процедура должна определять оператор, удалите ключевое слово `Implements` из ее объявления.  
  
## См. также  
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)