---
title: "Условный (троичный) оператор (?:) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>Условный (тернарный) оператор (?:) (JavaScript)
Возвращает одно из двух выражений в зависимости от условия.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Параметры  
 `test`  
 Любое логическое выражение.  
  
 `expression1`  
 Выражение, возвращаемое в том случае, если `test` равен `true`. Может быть выражением с запятыми.  
  
 `expression2`  
 Выражение, возвращаемое в том случае, если `test` равен `false`. С помощью запятой можно связать несколько выражений.  
  
## <a name="remarks"></a>Примечания  
 Оператор `?:` можно использовать в качестве ярлыка оператора `if...else`. Обычно его применяют в составе более крупного выражения, когда использовать оператор `if...else` нецелесообразно. Пример:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 В примере создается строка, содержащая «Good evening.» Если после 18: 00. Эквивалентный код с оператором `if...else` будет таким:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [If... else-оператор](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводка операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Приложение-пример сценария Junkie конфигурации мини-приложения](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)