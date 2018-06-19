---
title: Функция parseFloat (JavaScript) | Документы Microsoft
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
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638994"
---
# <a name="parsefloat-function-javascript"></a>Функция parseFloat (JavaScript)
Преобразует строку в число с плавающей запятой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `numString` аргументом является строка, содержащая число с плавающей запятой.  
  
 `parseFloat` Функция возвращает числовое значение, равное числу, содержащемуся в `numString`. Если префикс не `numString` успешно проанализировать число с плавающей запятой, `NaN` возвращается (не число).  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Можно проверить `NaN` с помощью `isNaN` функции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Функция parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)