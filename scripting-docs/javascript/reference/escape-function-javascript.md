---
title: "Функция escape (JavaScript) | Документы Microsoft"
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
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>Функция escape (JavaScript)
Кодирует строки, поэтому их можно прочитать на всех компьютерах. Не рекомендуется.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `charString` — это `String` объекта или литерала для кодирования.  
  
 **Escape** функция возвращает строковое значение (в формате Юникод), содержащее содержимое `charstring`. Все пробелы, знаки препинания, надстрочными знаками символов и не ASCII символы заменяются `%` *xx* кодирования, где *xx* эквивалентен шестнадцатеричное число, представляющее символ. Например пробел возвращается в виде «% 20».  
  
 Знаки, значения больше 255 хранятся с использованием **%u** *xxxx* формат.  
  
> [!NOTE]
>  **Escape** функция не должна использоваться для кодирования универсальных кодов ресурса (URI). Используйте `encodeURI` и `encodeURIComponent` вместо функции.  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Функция unescape](../../javascript/reference/unescape-function-javascript.md)