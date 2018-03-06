---
title: "Остаток от деления оператор присваивания (JavaScript) | Документы Microsoft"
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
- '%='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '%= operator [JavaScript]'
- remainder assignment operator [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9147ffbc-b598-4c44-b8f3-7b57914f6e9f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be7db43931374a71672c42ae059767585a9a5757
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="remainder-assignment-operator--javascript"></a>Оператор присваивания остатка (JavaScript)
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
 [Оператор остатка](../../javascript/reference/modulus-operator-decrementjavascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)