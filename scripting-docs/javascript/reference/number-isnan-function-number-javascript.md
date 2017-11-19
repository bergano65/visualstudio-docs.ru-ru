---
title: "Функция Number.isNaN (Number) (JavaScript) | Документы Microsoft"
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Функция Number.isNaN (Number) (JavaScript)
Возвращает логическое значение, указывающее, является ли значение зарезервированным значением `NaN` (не числом).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Параметры  
 `numValue`  
 Обязательный. Значение для проверки с использованием `NaN`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если значение преобразуется в тип `Number`, `true` имеет значение `NaN`; в противном случае — `false`.  
  
## <a name="remarks"></a>Примечания  
 Обычно этот метод используется для проверки значений, возвращаемых методами `parseInt` и `parseFloat`.  
  
 `Number.isNaN` устраняет проблемы с глобальной функцией `isNaN`. `Number.isNaN` только преобразует аргумент в тип Number, сравнив его с `NaN`. В результате `true` возвращается только в том случае, если переданный аргумент имеет точно такое же значение, что и `NaN`. Глобальная функция `isNaN` преобразует аргумент в тип Number до сравнения, в результате чего нечисловые значения могут возвращать значение `true`, но не выдавать значение `true` для `Number.isNaN`.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применяется к**: [число объектов](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Пример  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```