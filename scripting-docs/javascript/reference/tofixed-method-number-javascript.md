---
title: "Метод toFixed (Number) (JavaScript) | Документы Microsoft"
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>Метод toFixed (Number) (JavaScript)
Представляет число в нотации с фиксированной запятой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Параметры  
 `numObj`  
 Требуется объект `Number` объекта.  
  
 `fractionDigits`  
 Необязательно. Количество цифр после десятичной запятой. Должен быть в диапазоне 0 - 20, включительно.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает строковое представление числа в нотации с фиксированной запятой, содержащий `fractionDigits` цифр после десятичной запятой.  
  
 Если `fractionDigits` не указано или **не определено**, значение по умолчанию равно нулю.  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `toFixed`.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [число объектов](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Метод toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)