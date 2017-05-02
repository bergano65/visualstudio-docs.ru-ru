---
title: "Оператор присваивания сложения (+=) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "оператор присваивания сложения (+=)"
  - "+= - оператор"
  - "операторы присваивания, JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Оператор присваивания сложения (+=) (JavaScript)
Прибавляет значение выражения к значению переменной и присваивает результат переменной.  
  
## Синтаксис  
  
```  
  
result += expression   
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Произвольное выражение.  
  
## Заметки  
 Использование данного оператора полностью эквивалентно следующему выражению: `result = result + expression`.  
  
 Типы двух выражений определяют поведение оператора `+=`.  
  
|Если|Тогда|  
|----------|-----------|  
|Оба выражения являются числовыми или логическими|Сложение|  
|Оба выражения представляют собой строки|Объединение|  
|Одно выражение числовое, а второе — строка|Объединение|  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор сложения \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)