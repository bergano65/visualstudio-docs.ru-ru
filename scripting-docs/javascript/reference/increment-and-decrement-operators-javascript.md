---
title: "Операторы увеличения (++) и уменьшения (--) (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "операторы инкремента, синтаксис"
  - "++ - оператор"
  - "оператор ++, сведения об операторе ++"
  - "операторы декремента, синтаксис"
  - "-- - оператор"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Операторы увеличения (++) и уменьшения (--) (JavaScript)
Оператор инкремента увеличивает, а оператор декремента уменьшает значение переменной на единицу.  
  
## Синтаксис  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `variable`  
 Любая переменная.  
  
## Заметки  
 Если оператор располагается перед переменной, это значение изменяется до того, как вычисляется выражение.  Если оператор располагается после переменной, это значение изменяется после того, как вычисляется выражение.  Иначе говоря, в выражении `j = ++k;` значение `j` равняется исходному значению `k` плюс один, а в выражении `j = k++;` значение `j` равняется исходному `k`, которое увеличивается уже после присваивания переменной `j`.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)