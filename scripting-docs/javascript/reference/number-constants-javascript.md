---
title: Число константы (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639204"
---
# <a name="number-constants-javascript"></a>Числовые константы (JavaScript)
Следующие числовые константы являются свойствами объекта `Number`.  
  
## <a name="number-object-constants"></a>Числовые константы объекта  
 Для доступа к этим константам не обязательно создавать объект `Number`.  
  
|Константа|Возвращаемое значение|  
|--------------|--------------------|  
|`Number.EPSILON`|Наименьшее число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Приблизительно равно 2,2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Наибольшее число, представимое в JavaScript. Равно 9007199254740991.|  
|`Number.MAX_VALUE`|Наибольшее число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Приблизительно равно 1,79E+308.|  
|`Number.MIN_SAFE_INTEGER`|Наименьшее число, представимое в JavaScript. Равно-9007199254740991.|  
|`Number.MIN_VALUE`|Самое близкое к нулю число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Приблизительно равно 5,00E-324.|  
|`Number.NaN`|Значение, которое не является числом.<br /><br /> В сравнениях на равенство `NaN` не будет равно ни одному числу, включая себя же. Чтобы проверить, является ли значение эквивалентным `NaN`, используйте [функцию isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Значение, меньшее самого крупного отрицательного числа, представимого в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отображает значения `NEGATIVE_INFINITY` как `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Число, большее самого большого числа, представимого в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отображает значения `POSITIVE_INFINITY` как `infinity`.|  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Для `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` и `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применяется к**: [число объектов](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Математические константы](../../javascript/reference/math-constants-javascript.md)   
 [Константы JavaScript](../../javascript/reference/javascript-constants.md)   
 [Константа Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [Константа NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)