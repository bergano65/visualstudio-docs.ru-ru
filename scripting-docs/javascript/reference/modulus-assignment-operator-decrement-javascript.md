---
title: "Оператор присваивания модуля (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '%= operator [JavaScript]'
- modulus assignment operator [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9147ffbc-b598-4c44-b8f3-7b57914f6e9f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c61a0fda53b50146f25a8e9c2e04dba9490c494c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="modulus-assignment-operator--javascript"></a>оператор присваивания модуля (JavaScript)
Делит значение переменной на значение выражения и присваивает остаток переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result %= expression  
```  
  
## <a name="arguments"></a>Аргументы  
 `result`  
 Любая переменная.  
  
 `expression`  
 Произвольное числовое выражение.  
  
## <a name="remarks"></a>Примечания  
 Использование оператора `%=` полностью эквивалентно следующему выражению:  
  
```  
result = result % expression  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор остатка от деления](../../javascript/reference/modulus-operator-decrementjavascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)