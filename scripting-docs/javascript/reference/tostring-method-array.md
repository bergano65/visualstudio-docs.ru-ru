---
title: "Метод toString (Array) | Документы Microsoft"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-array"></a>Метод toString (Array)
Возвращает строковое представление массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Параметры  
 `array`  
 Обязательный. Массив, для представления в виде строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строковое представление массива.  
  
## <a name="remarks"></a>Примечания  
 Элементы `Array` преобразуются в строки. Результирующие строки объединяются и разделенные запятыми.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **toString** метод с массивом.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]