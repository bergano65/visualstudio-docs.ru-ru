---
title: "Метод toPrecision (Number) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>Метод toPrecision (Number) (JavaScript)
Представляет число, либо в экспоненциальной нотации с указанного количества десятичных разрядов с фиксированной запятой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Параметры  
 `numObj`  
 Обязательный. Объект `Number`.  
  
 `precision`  
 Необязательно. Количество значащих цифр. Должен быть в диапазоне 1-21 включительно.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Для чисел в экспоненциальной нотации `precision` - 1 возвращается цифр после десятичной запятой. Для чисел в фиксированной нотацией `precision` возвращаются значащих цифр.  
  
 Если `precision` не указан или является **не определено**, **toString** вызывается метод.  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `toPrecision`.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [число объектов](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toFixed (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)