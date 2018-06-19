---
title: Метод charAt (String) (JavaScript) | Документы Microsoft
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634134"
---
# <a name="charat-method-string-javascript"></a>Метод charAt (строка) (JavaScript)
Возвращает знак с указанным индексом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Параметры  
 `strObj`  
 Обязательный. Любой `String` или строковый литерал.  
  
 `index`  
 Обязательный. Отсчитываемый от нуля индекс требуемого символа.  
  
## <a name="remarks"></a>Примечания  
 `charAt` Метод возвращает значение символа знака из указанного `index`. Первый символ в строке по индексу 0, второй — с индексом 1 и т. д. Значения `index` , выходят за пределы диапазона возвращаемого пустая строка.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `charAt` метода:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)