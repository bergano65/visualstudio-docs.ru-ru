---
title: "Переменные с ключевым словом WithEvents должны иметь предложение As. | Microsoft Docs"
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
  - "vbc30412"
  - "bc30412"
helpviewer_keywords: 
  - "BC30412"
ms.assetid: 8c941523-8e5d-4bf0-8a52-772ecd5d5592
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменные с ключевым словом WithEvents должны иметь предложение As.
Не предоставлено предложение `As` с ключевым словом `WithEvents`. Объявите переменную как определенный класс, который может инициировать события.  
  
 **Идентификатор ошибки:** BC30412  
  
### Исправление ошибки  
  
1.  Добавьте предложение `As`, указывающее класс, который может инициировать события.  
  
## См. также  
 [НЕ В СБОРКЕ. Оператор WithEvents и предложение Handles](http://msdn.microsoft.com/ru-ru/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)