---
title: "Переменные с ключевым словом &quot;WithEvents&quot; могут быть типизированы как классы, интерфейсы и параметры типа с ограничениями класса | Microsoft Docs"
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
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменные с ключевым словом &quot;WithEvents&quot; могут быть типизированы как классы, интерфейсы и параметры типа с ограничениями класса
Объявлена переменная, которая типизирована как структура в сочетании с `WithEvents`, что является недопустимым использованием модификатора `WithEvents`.  
  
 **Идентификатор ошибки:** BC30413  
  
### Исправление ошибки  
  
1.  Используйте `AddHandler` для обработки событий, определенных в структуре.  
  
## См. также  
 [НЕ В СБОРКЕ. Оператор WithEvents и предложение Handles](http://msdn.microsoft.com/ru-ru/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)