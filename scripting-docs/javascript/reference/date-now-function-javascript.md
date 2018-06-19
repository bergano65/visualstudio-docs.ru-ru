---
title: Функция Date.Now (JavaScript) | Документы Microsoft
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
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636394"
---
# <a name="datenow-function-javascript"></a>Функция Date.now (JavaScript)
Возвращает текущую дату и время.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Количество миллисекунд, истекших с полуночи 1 января 1970 года и текущей датой и временем.  
  
## <a name="remarks"></a>Примечания  
 [GetTime-метод](../../javascript/reference/gettime-method-date-javascript.md) возвращает число миллисекунд, истекших с 1 января 1970 года и указанной даты.  
  
 Сведения о том, как для вычисления истекшего времени и для сравнения дат в разделе [вычисления даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `now`.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Требования  
 Не поддерживается в установленных версий более ранних, чем Internet Explorer 9. Тем не менее, он поддерживается в следующих режимах документов: случайный стандартов Internet Explorer 6, стандартов Internet Explorer 7, Internet Explorer 8, стандартный, стандартов Internet Explorer 9, Internet Explorer 10, стандартный. Также поддерживается в [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] приложений.  
  
## <a name="see-also"></a>См. также  
 [Метод getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Вычисление даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)