---
title: "Функция Array.of (Array) (JavaScript) | Документы Microsoft"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="arrayof-function-array-javascript"></a>Функция Array.of (Array) (JavaScript)
Возвращает массив из переданных аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `element0,...,elementN`  
 Необязательно. Элементы, размещаемые в массиве. Создает массив с числом элементов n + 1 и значением length, равным n + 1.  
  
## <a name="remarks"></a>Примечания  
 Эта функция работает как вызов `new Array(args)`, однако `Array.of` не определяет особое поведение в случае передачи одного аргумента.  
  
## <a name="example"></a>Пример  
 В следующем примере создается массив из переданных чисел.  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано различие между использованием `Array.of` и `new Array`.  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]