---
title: "Оператор вычитания (-) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Оператор вычитания (-) (JavaScript)
Вычитает значение одного выражения из другого или операцию унарного отрицания из одного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любой числовой переменной.  
  
 `number`  
 Произвольное числовое выражение.  
  
 `number1`  
 Произвольное числовое выражение.  
  
 `number2`  
 Произвольное числовое выражение.  
  
## <a name="remarks"></a>Примечания  
 В синтаксисе 1  **-**  оператор — оператор арифметического вычитания, позволяет определить разницу между двумя числами. В синтаксисе 2  **-**  оператор используется как оператор унарного отрицания для обозначения отрицательного значения выражения.  
  
 Для синтаксиса 2 как и для всех унарных операторов, вычисляются следующим образом:  
  
-   Если применяется не определен или `null` возникает выражения, ошибка времени выполнения.  
  
-   Объекты преобразуются в строки.  
  
-   Строки преобразуются в числа, если это возможно. В противном случае возникает ошибка времени выполнения.  
  
-   Логические значения обрабатываются как числа (0, если значение равно false, 1, если значение true).  
  
 Оператор применяется к результирующему числу. В синтаксисе 2, если результирующее число равно нулю *результат* равно результирующее число с обратным знаком. Если результирующее число равно нулю, *результат* равно нулю.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания вычитания (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)