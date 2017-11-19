---
title: "Оператор сложения (+) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Оператор сложения (+) (JavaScript)
Добавляет значение одного числового выражения на другой или объединяет две строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression1`  
 Любое выражение.  
  
 `expression2`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Типы двух выражений определяют поведение  **+**  оператор.  
  
|If|Следующее действие|  
|--------|----------|  
|Оба выражения имеют числовые или логические|Добавить|  
|Оба выражения представляют собой строки|Объединение|  
|Одно выражение является числовым, а второе — строка.|Объединение|  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания сложения (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)