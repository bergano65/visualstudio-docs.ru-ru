---
title: "Оператор логического ИЛИ (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| - оператор"
  - "логический оператор OR (||)"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор логического ИЛИ (||) (JavaScript)
Выполняет логическое сложение двух выражений.  
  
## Синтаксис  
  
```  
  
result = expression1 || expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Если любое из выражений или оба выражения имеют значение **True**, результат *result* равен **True**.  В следующей таблице показано, как определяется результат *result*.  
  
|Если `expression1` имеет значение|И выражение `expression2` имеет значение|Результат `result` имеет значение|  
|---------------------------------------|----------------------------------------------|---------------------------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует следующие правила для преобразования нелогических значений в логические.  
  
-   Предполагается, что все объекты являются значениями true.  
  
-   Строки считаются значениями false только в том случае, если они пустые.  
  
-   Значения `null` и undefined рассматриваются как значения false.  
  
-   Цифры считаются значениями false только в том случае, если они равны 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)