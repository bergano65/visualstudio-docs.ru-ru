---
title: Оператор let (JavaScript) | Документы Microsoft
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638894"
---
# <a name="let-statement-javascript"></a>Оператор let (JavaScript)
Объявляет переменную с областью видимости, ограниченной блоком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Параметры  
 `variable1`  
 Имя объявляемой переменной.  
  
 `value1`  
 Начальное значение, присвоенное переменной.  
  
## <a name="remarks"></a>Примечания  
 Используйте `let` инструкции для объявления переменной, область которого ограничена блока, в котором она объявлена. Можно назначить значения переменным, при их объявлении или более поздней версии в сценарии.  
  
 Переменная, объявленная с помощью `let` не может использоваться до приведет к ее объявления или ошибку.  
  
 Если вы не инициализировать переменную в `let` инструкции, автоматически назначается [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] значение `undefined`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `let`.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор Const](../../javascript/reference/const-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)