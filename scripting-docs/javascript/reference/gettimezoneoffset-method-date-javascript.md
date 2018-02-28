---
title: "Метод getTimezoneOffset (Date) (JavaScript) | Документы Microsoft"
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>Метод getTimezoneOffset (Date) (JavaScript)
Возвращает разницу в минутах между временем на локальном компьютере и в формате общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает количество минут между временем на текущем компьютере (клиентском компьютере или, если этот метод вызывается из серверного скрипта, компьютер сервера) и в формате UTC. Является положительным местного времени текущего компьютера отстает от UTC (например, тихоокеанское летнее время), а отрицательное местного времени текущего компьютера в случае опережают время UTC (например, Япония). Если связаться с сервером в Нью-Йорке, клиентом в Лос-Анджелес 1 декабря `getTimezoneOffset` возвращает 480, если выполняется на стороне клиента или 300, если выполняются на сервере.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getTimezoneOffset`.  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)