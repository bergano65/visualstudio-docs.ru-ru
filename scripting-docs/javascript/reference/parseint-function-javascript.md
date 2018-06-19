---
title: Функция parseInt (JavaScript) | Документы Microsoft
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
- parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639614"
---
# <a name="parseint-function-javascript"></a>Функция parseInt (JavaScript)
Преобразует строку в целое число.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Параметры  
 `numString`  
 Обязательный. Строка для преобразования в число.  
  
 `radix`  
 Необязательно. Значение в диапазоне от 2 до 36, который задает основание системы счисления в `numString`. Если этот аргумент не указан, считаются шестнадцатеричных строк с префиксом "0 x». Все остальные строки считаются десятичными числами.  
  
## <a name="remarks"></a>Примечания  
 `parseInt` Функция возвращает целочисленное значение, равное числу, содержащемуся в `numString`. Если префикс не `numString` может быть проанализирован успешно в целое число, `NaN` возвращается (не число).  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Можно проверить `NaN` с помощью `isNaN` функции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  Начиная с версии [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], `parseInt` функция не обрабатывать строка с префиксом "0" как восьмеричное. Если вы не используете `parseInt` работать, однако строки с префиксом "0" можно по-прежнему интерпретируются как восьмеричные числа. В разделе [типы данных](../../javascript/data-types-javascript.md) сведения о восьмеричные целые числа.  
  
## <a name="see-also"></a>См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Функция parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Метод valueOf (Object)](../../javascript/reference/valueof-method-object-javascript.md)