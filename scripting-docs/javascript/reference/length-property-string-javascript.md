---
title: Свойство Length (строка) (JavaScript) | Документы Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638174"
---
# <a name="length-property-string-javascript"></a>Свойство length (строка) (JavaScript)
Возвращает длину объекта `String`.  
  
> [!WARNING]
>  JavaScript строки являются неизменяемыми, поэтому невозможно изменить длину строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Примечания  
 `length` Свойство содержит целое число, указывающее количество символов в `String` объекта. Последний символ в `String` объект имеет индекс я`length` - 1.  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `length`. JavaScript строки являются неизменяемыми и не может быть изменен. Тем не менее, можно написать обратной строке в массив и затем вызвать метод `join` с пустой символ, которого формирует строку без символов разделителя.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]