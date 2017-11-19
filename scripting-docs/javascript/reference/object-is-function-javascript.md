---
title: "Функция Object.IS (JavaScript) | Документы Microsoft"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectis-function-javascript"></a>Функция Object.is (JavaScript)
Возвращает значение, определяющее, совпадают ли два значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>Параметры  
 `value1`  
 Обязательный. Первое значение для проверки.  
  
 `value2`  
 Обязательный. Второе значение для проверки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение `true`, если значения совпадают; в противном случае — значение `false`.  
  
## <a name="remarks"></a>Примечания  
 В отличие от оператора ==, функция `Object.is` не приводит проверяемые значения к каким-либо типам.  
  
 Функция `Object.is` применяет такое же сравнение, что и оператор ===, за исключением случаев, когда `Object.is` считает, что значение `Number.isNaN` совпадает со значением `NaN`. Кроме того, она обрабатывает +0 и –0 как разные значения.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]