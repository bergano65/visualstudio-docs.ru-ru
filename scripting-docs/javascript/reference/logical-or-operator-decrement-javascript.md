---
title: "Логический оператор (|) или (JavaScript) | Документы Microsoft"
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
- '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>Оператор логического ИЛИ (||) (JavaScript)
Выполняет логическое разделение двух выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *expression1*  
 Любое выражение.  
  
 *Expression2*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Если один или оба выражения **True**, *результат* — **True**. В следующей таблице показано, как *результат* определяется:  
  
|Если `expression1` является|И `expression2` —|`result` —|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует следующие правила для преобразования нелогических значений в логические значения.  
  
-   Все объекты считаются значение true.  
  
-   Строки считаются false только в том случае, если они являются пустыми.  
  
-   `null`и неопределенный считаются значение false.  
  
-   Числа являются значение false, если и только при условии, они равны 0.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)