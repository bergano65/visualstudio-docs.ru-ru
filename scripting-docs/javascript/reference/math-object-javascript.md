---
title: Math-объект (JavaScript) | Документы Microsoft
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
- Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642164"
---
# <a name="math-object-javascript"></a>Объект Math (JavaScript)
Встроенный объект, предоставляющий основные математические функции и константы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>Параметры  
 *Свойство*  
 Обязательный. Имя одного из свойств **математические**. .  
  
 *метод*  
 Обязательный. Имя одного из методов **математические**. .  
  
## <a name="remarks"></a>Примечания  
 **Математические** не удается создать объект с помощью **новый** оператор и выдает ошибку при попытке сделать это. Обработчик скриптов создает объект при загрузке обработчика. Все его методы и свойства доступны вашему скрипту в любое время.  
  
## <a name="requirements"></a>Требования  
 Объект `Math` появился в [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Math`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа Math.E](../../javascript/reference/math-constants-javascript.md)|Математическая константа e. Это число Эйлера, основа натуральных логарифмов.|  
|[Константа Math.LN2](../../javascript/reference/math-constants-javascript.md)|Натуральный логарифм числа 2.|  
|[Константа Math.LN10](../../javascript/reference/math-constants-javascript.md)|Натуральный логарифм числа 10.|  
|[Константа Math.LOG2E](../../javascript/reference/math-constants-javascript.md)|Логарифм числа e по основанию 2.|  
|[Константа Math.LOG10E](../../javascript/reference/math-constants-javascript.md)|Логарифм числа e по основанию 10.|  
|[Константа Math.PI](../../javascript/reference/math-constants-javascript.md)|Число Пи. Отношение длины окружности к ее диаметру.|  
|[Константа Math.SQRT1_2](../../javascript/reference/math-constants-javascript.md)|Квадратный корень из 0,5 или единица, деленная на квадратный корень числа 2.|  
|[Константа Math.SQRT2](../../javascript/reference/math-constants-javascript.md)|Квадратный корень из 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>Функции  
 В следующей таблице перечислены функции объекта `Math`.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[Функция Math.abs](../../javascript/reference/math-abs-function-javascript.md)|Возвращает абсолютное значение числа.|  
|[Функция Math.acos](../../javascript/reference/math-acos-function-javascript.md)|Возвращает арккосинус числа.|  
|[Функция Math.acosh](../../javascript/reference/math-acosh-function-javascript.md)|Возвращает гиперболический арккосинус (или обратный гиперболический косинус) числа.|  
|[Функция Math.asin](../../javascript/reference/math-asin-function-javascript.md)|Возвращает арксинус числа.|  
|[Функция Math.asinh](../../javascript/reference/math-asinh-function-javascript.md)|Возвращает ареа-синус числа.|  
|[Функция Math.atan](../../javascript/reference/math-atan-function-javascript.md)|Возвращает арктангенс числа.|  
|[Функция Math.atan2](../../javascript/reference/math-atan2-function-javascript.md)|Возвращает угол (в радианах) от оси X до точки, соответствующей указанным координатам X и Y.|  
|[Функция Math.atanh](../../javascript/reference/math-atanh-function-javascript.md)|Возвращает ареа-тангенс числа.|  
|[Функция Math.ceil](../../javascript/reference/math-ceil-function-javascript.md)|Возвращает наименьшее целое число, которое больше заданного числового выражения или равно ему.|  
|[Функция Math.cos](../../javascript/reference/math-cos-function-javascript.md)|Возвращает косинус числа.|  
|[Функция Math.cosh](../../javascript/reference/math-cosh-function-javascript.md)|Возвращает гиперболический косинус числа.|  
|[Функция Math.exp](../../javascript/reference/math-exp-function-javascript.md)|Возвращает *e* (основание натуральных логарифмов), возведенное в степень.|  
|[Функция Math.expm1](../../javascript/reference/math-expm1-function-javascript.md)|Возвращает результат вычитания 1 из e (основания натуральных логарифмов), возведенного в степень.|  
|[Функция Math.floor](../../javascript/reference/math-floor-function-javascript.md)|Возвращает наибольшее целое число, которое меньше заданного числового выражения или равно ему.|  
|[Функция Math.hypot](../../javascript/reference/math-hypot-function-javascript.md)|Возвращает квадратный корень из суммы квадратов аргументов.|  
|[Функция Math.imul](../../javascript/reference/math-imul-function-javascript.md)|Возвращает произведение двух чисел, которые обрабатываются как 32-разрядные целые числа со знаком.|  
|[Функция Math.log](../../javascript/reference/math-log-function-javascript.md)|Возвращает натуральный логарифм числа.|  
|[Функция Math.log1p](../../javascript/reference/math-log1p-function-javascript.md)|Возвращает натуральный логарифм 1 плюс числа.|  
|[Функция Math.log10](../../javascript/reference/math-log10-function-javascript.md)|Возвращает логарифм с основанием 10 числа.|  
|[Функция Math.log2](../../javascript/reference/math-log2-function-javascript.md)|Возвращает логарифм с основанием 2 числа.|  
|[Функция Math.max](../../javascript/reference/math-max-function-javascript.md)|Возвращает большее из двух заданных числовых выражений.|  
|[Функция Math.min](../../javascript/reference/math-min-function-javascript.md)|Возвращает меньшее из двух заданных чисел.|  
|[Функция Math.pow](../../javascript/reference/math-pow-function-javascript.md)|Возвращает значение базового выражения, возведенного в заданную степень.|  
|[Функция Math.random](../../javascript/reference/math-random-function-javascript.md)|Возвращает псевдослучайное число от 0 до 1.|  
|[Функция Math.round](../../javascript/reference/math-round-function-javascript.md)|Возвращает указанное числовое выражение, округленное до ближайшего целого числа.|  
|[Функция Math.sign](../../javascript/reference/math-sign-function-javascript.md)|Возвращает знак числа, указывающий, является ли число положительным, отрицательным или равным 0.|  
|[Функция Math.sin](../../javascript/reference/math-sin-function-javascript.md)|Возвращает синус числа.|  
|[Функция Math.sinh](../../javascript/reference/math-sinh-function-javascript.md)|Возвращает ареа-синус числа.|  
|[Функция Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Возвращает квадратный корень числа.|  
|[Функция Math.tan](../../javascript/reference/math-tan-function-javascript.md)|Возвращает тангенс числа.|  
|[Функция Math.tanh](../../javascript/reference/math-tanh-function-javascript.md)|Возвращает гиперболический тангенс числа.|  
|[Функция Math.trunc](../../javascript/reference/math-trunc-function-javascript.md)|Возвращает целую часть числа, отбросив все цифры дробной части.|  
  
## <a name="see-also"></a>См. также  
 [Объекты JavaScript](../../javascript/reference/javascript-objects.md)   
 [Объект Number](../../javascript/reference/number-object-javascript.md)