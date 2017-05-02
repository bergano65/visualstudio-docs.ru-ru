---
title: "Числовые константы (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "константы [JavaScript], числовые"
  - "MAX_VALUE - константа [JavaScript]"
  - "MIN_VALUE - константа [JavaScript]"
  - "NaN - константа [JavaScript]"
  - "NEGATIVE_INFINITY - константа [JavaScript]"
  - "числовые константы [JavaScript]"
  - "Number.MAX_VALUE - константа [JavaScript]"
  - "Number.MIN_VALUE - константа [JavaScript]"
  - "Number.NaN - константа [JavaScript]"
  - "Number.NEGATIVE_INFINITY - константа [JavaScript]"
  - "Number.POSITIVE_INFINITY - константа [JavaScript]"
  - "POSITIVE_INFINITY - константа [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Числовые константы (JavaScript)
Следующие числовые константы являются свойствами объекта `Number`.  
  
## Числовые константы объекта  
 Для доступа к этим константам не обязательно создавать объект `Number`.  
  
|Константа|Возвращаемое значение|  
|---------------|---------------------------|  
|`Number.EPSILON`|Наименьшее число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Приблизительно равно 2,2204460492503130808472633361816E\-16.|  
|`Number.MAX_SAFE_INTEGER`|Наибольшее число, представимое в JavaScript.  Равно 9007199254740991.|  
|`Number.MAX_VALUE`|Наибольшее число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Приблизительно равно 1,79E\+308.|  
|`Number.MIN_SAFE_INTEGER`|Наименьшее число, представимое в JavaScript.  Равно −9007199254740991.|  
|`Number.MIN_VALUE`|Самое близкое к нулю число, представимое в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Приблизительно равно 5,00E\-324.|  
|`Number.NaN`|Значение, которое не является числом.<br /><br /> В сравнениях на равенство `NaN` не будет равно ни одному числу, включая себя же.  Чтобы проверить, является ли значение эквивалентным `NaN`, используйте [функцию isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Значение, меньшее самого крупного отрицательного числа, представимого в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отображает значения `NEGATIVE_INFINITY` как `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Число, большее самого большого числа, представимого в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отображает значения `POSITIVE_INFINITY` как `infinity`.|  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Для `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` и `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применение**: [Объект Number](../../javascript/reference/number-object-javascript.md)  
  
## См. также  
 [Математические константы](../../javascript/reference/math-constants-javascript.md)   
 [Константы JavaScript](../../javascript/reference/javascript-constants.md)   
 [Константа Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [Константа NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)