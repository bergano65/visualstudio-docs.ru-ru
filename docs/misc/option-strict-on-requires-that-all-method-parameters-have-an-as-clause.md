---
title: "Оператор &quot;Option Strict On&quot; требует, чтобы все параметры метода имели предложение As | Microsoft Docs"
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
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;Option Strict On&quot; требует, чтобы все параметры метода имели предложение As
Метод содержит параметр без предложения `As`. Когда директива `Option Strict` имеет значение on, все переменные, свойства, аргументы процедур и возвращаемые значения функций должны быть объявлены с предложением `As` для указания типа данных, например `Sub GetData(ByVal filter As String)`.  
  
 **Идентификатор ошибки:** BC30211  
  
### Исправление ошибки  
  
-   Проверьте правильность написания ключевого слова `As`.  
  
-   Укажите предложение `As` для объявленной переменной или укажите директиву `Option Strict` со значением off.  
  
## См. также  
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Оператор Sub](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement)