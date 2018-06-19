---
title: Остаток от деления оператор (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639574"
---
# <a name="remainder-operator-javascript"></a>Оператор остатка (JavaScript)
Делит значение одного выражения значение другого и возвращает остаток.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Аргументы  
 `result`  
 Любая переменная.  
  
 `number1`  
 Произвольное числовое выражение.  
  
 `number2`  
 Произвольное числовое выражение.  
  
## <a name="remarks"></a>Примечания  
 Оператор остатка делит `number1` по `number2`и возвращает только остаток как `result`. Знак `result` совпадает со знаком `number1`. Значение `result` находится между 0 и абсолютное значение `number2`.  
  
 Ниже показано, как использовать оператор остатка.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
