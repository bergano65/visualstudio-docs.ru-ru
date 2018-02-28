---
title: "Оператор Const (JavaScript) | Документы Microsoft"
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>Оператор const (JavaScript)
Объявляет переменную с областью видимости, ограниченной блоком, с постоянным значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Параметры  
 `constant1`  
 Имя объявляемой переменной.  
  
 `value1`  
 Начальное значение, присвоенное переменной.  
  
## <a name="remarks"></a>Примечания  
 Используйте `const` инструкции для объявления переменной со значением константы, область которого ограничена блока, в котором она объявлена. Не удается изменить значение переменной.  
  
 Переменная, объявленная с помощью `const` должны инициализироваться при их объявлении.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `const`.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор let](../../javascript/reference/let-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)