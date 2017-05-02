---
title: "Оператор сложения (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "арифметические операторы, сложение"
  - "строки [Visual Studio], объединение"
  - "операторы объединения, в сравнении с оператором сложения"
  - "оператор сложения"
  - "+ - оператор"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Оператор сложения (+) (JavaScript)
Складывает значение одного числового выражения с другим или объединяет две строки.  
  
## Синтаксис  
  
```  
  
result = expression1 + expression2  
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `expression1`  
 Произвольное выражение.  
  
 `expression2`  
 Произвольное выражение.  
  
## Заметки  
 Типы двух выражений определяют поведение оператора **\+**.  
  
|Если|Тогда|  
|----------|-----------|  
|Оба выражения являются числовыми или логическими|Сложение|  
|Оба выражения представляют собой строки|Объединение|  
|Одно выражение числовое, а второе — строка|Объединение|  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания сложения \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)