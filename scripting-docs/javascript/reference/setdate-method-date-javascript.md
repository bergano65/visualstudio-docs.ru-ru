---
title: "Метод setDate (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>Метод setDate (Date) (JavaScript)
Задает числовое значение дня месяца `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numDate`  
 Обязательный. Числовое значение, обозначающее день месяца.  
  
## <a name="remarks"></a>Примечания  
 Чтобы установить значение дня месяца, с помощью общего скоординированного времени (UTC), используйте `setUTCDate` метод.  
  
 Если значение `numDate` больше, чем число дней в месяце, передача даты за более поздней версии месяц или год. Например, если сохранена дата — 5 января 1996 г. и `setDate(32)` вызывается изменения даты на 1 февраля 1996 г. Если `numDate` является отрицательным числом, дата выполняет откат предыдущих месяц или год. Например, если сохранена дата — 5 января 1996 г. и `setDate(-32)` вызывается Дата изменения 29 ноября 1995 г.  
  
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md) может использоваться для задания год, месяц и день месяца.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `setDate`.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Метод setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)