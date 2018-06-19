---
title: If... else-оператор (JavaScript) | Документы Microsoft
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
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637334"
---
# <a name="ifelse-statement-javascript"></a>Оператор if...else (JavaScript)
Выполняет ту или иную группу операторов в зависимости от значения выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Параметры  
 `condition1`  
 Обязательный. Выражение типа Boolean. Если `condition1` — `null` или `undefined`, `condition1` рассматривается как `false`.  
  
 `statement1`  
 Необязательно. Инструкции для выполнения, если `condition1` — **true**. Может быть составным оператором.  
  
 `condition2`  
 Проверяемое условие.  
  
 `statement2`  
 Необязательно. Инструкции для выполнения, если `condition2` — `true`. Может быть составным оператором.  
  
 `statement3`  
 Если оба `condition1` и `condition2` , `false`, эта инструкция выполняется.  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `if`, `if else`, и `else`.  
  
 Рекомендуется заключать `statement1` и `statement2` в фигурные скобки ({}) для большей ясности и избежать случайных ошибок.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Условный (троичный) оператор (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)