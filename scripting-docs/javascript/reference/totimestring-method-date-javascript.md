---
title: Метод toTimeString (Date) (JavaScript) | Документы Microsoft
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640074"
---
# <a name="totimestring-method-date-javascript"></a>Метод toTimeString (Date) (JavaScript)
Возвращает время в виде строкового значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Примечания  
 Обязательная ссылка `objDate` — это объект `Date`.  
  
 `toTimeString` Метод возвращает строковое значение, содержащее время в текущем часовом поясе.  
  
## <a name="example"></a>Пример  
 В следующем примере время равно 2 000 миллисекунд после полуночи 1 января 1970 г. UTC и затем она записывается.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toDateString (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)