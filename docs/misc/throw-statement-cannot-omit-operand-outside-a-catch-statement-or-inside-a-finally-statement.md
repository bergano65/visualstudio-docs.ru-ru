---
title: "В операторе Throw запрещается опускать операнд вне оператора Catch и в операторе Finally | Microsoft Docs"
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
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В операторе Throw запрещается опускать операнд вне оператора Catch и в операторе Finally
В операторах `Throw`, находящихся вне оператора `Catch`, должно быть указано имя объекта исключения.  
  
 **Идентификатор ошибки:** BC30666  
  
### Исправление ошибки  
  
1.  Укажите имя объекта исключения, производного от класса `System.Exception`.  
  
2.  Измените структуру кода таким образом, чтобы оператор `Throw` находился внутри блока `Catch`.  
  
## См. также  
 [Оператор Throw](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Класс Exception в Visual Basic](http://msdn.microsoft.com/ru-ru/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)