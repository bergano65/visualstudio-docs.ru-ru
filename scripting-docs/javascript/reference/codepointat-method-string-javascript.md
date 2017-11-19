---
title: "Метод codePointAt (String) (JavaScript) | Документы Microsoft"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>Метод codePointAt (String) (JavaScript)
Возвращает кодовую точку для символа Юникода UTF-16.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Строковый объект.  
  
 `pos`  
 Обязательный. Позиция символа.  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает значения кодовых точек, включая астральные кодовые точки (кодовые точки с более чем четырьмя шестнадцатеричными значениями) для всех символов UTF-16.  
  
 Если `pos` меньше нуля (0) или больше размера строки, возвращаемое значение — `undefined`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `codePointAt`.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
