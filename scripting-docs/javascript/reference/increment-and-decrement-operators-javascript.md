---
title: (++) Операторы инкремента и декремента (--) (JavaScript) | Документы Microsoft
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
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637354"
---
# <a name="increment--and-decrement----operators-javascript"></a>Операторы увеличения (++) и уменьшения (--) (JavaScript)
Увеличивает оператор инкремента и декремента оператор уменьшает значение переменной на единицу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `variable`  
 Любая переменная.  
  
## <a name="remarks"></a>Примечания  
 Если оператор отображается перед переменной, изменить это значение перед вычислением выражения. Если оператор находится после переменной, изменить это значение после вычисления выражения.  Другими словами, учитывая `j = ++k;`, значение `j` представляет собой исходное значение из `k` плюс один; заданному `j = k++;`, значение `j` представляет собой исходное значение из `k`, которого увеличивается после его значение будет назначено `j`.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)