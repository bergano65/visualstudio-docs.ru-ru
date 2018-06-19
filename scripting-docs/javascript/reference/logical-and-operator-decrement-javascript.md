---
title: Оператор логического и (&amp;&amp;) (JavaScript) | Документы Microsoft
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
- '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638284"
---
# <a name="logical-and-operator-ampamp-javascript"></a>Оператор логического и (&amp;&amp;) (JavaScript)
Выполняет логическое умножение двух выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression1`  
 Любое выражение.  
  
 `expression2`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Если `expression1` равно `false`, `result` равно `expression1`. В противном случае `result` является `expression2`. Следовательно, операция возвращает `true`, если оба операнда имеют значение true. В противном случае возвращается `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует следующие правила для преобразования нелогических значений в логические значения.  
  
-   Все объекты считаются `true`.  
  
-   Строки считаются `false`, если они пусты.  
  
-   `null` и `undefined` считаются `false`.  
  
-   Число является `false`, если оно равно нулю.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)