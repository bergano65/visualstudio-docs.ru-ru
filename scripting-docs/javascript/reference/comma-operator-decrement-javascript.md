---
title: "Оператор \"запятая\" (,) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="comma-operator--javascript"></a>Оператор "запятая" (,) (JavaScript)
Приводит к последовательному выполнению двух выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Параметры  
 `expression1`  
 Любое выражение.  
  
 `expression2`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 `,` Оператор вызывает выражения для выполнения в порядке слева направо. Обычно используются для `,` оператор находится в выражении увеличения `for` цикла. Например:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for` Оператор разрешает только одно выражение для выполнения в конце каждого прохода цикла. `,` Оператор позволяет несколько выражений, следует рассматривать как одного выражения, поэтому обе переменные может быть увеличен.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)