---
title: "Функция Math.imul (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathimul-function-javascript"></a>Функция Math.imul (JavaScript)
Возвращает произведение двух чисел, которые обрабатываются как 32-разрядные целые числа со знаком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Параметры  
 `x`  
 Обязательный. Первое число.  
  
 `y`  
 Обязательный. Второе число.  
  
## <a name="remarks"></a>Примечания  
 Эта функция используется для компиляторов, таких как Emscripten и Mandreel, в которых умножение целых чисел реализовано не так, как в JavaScript.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как выполнять умножение с помощью функции `Math.imul`.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]