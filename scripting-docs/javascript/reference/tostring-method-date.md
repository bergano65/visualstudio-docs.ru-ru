---
title: "Метод toString (Date) | Документы Microsoft"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-date"></a>Метод toString (Date)
Возвращает строковое представление даты. Формат строки зависит от языкового стандарта. В США Английский (en-us), он выглядит следующим образом:  
  
 *день недели* *месяц* *день* *час*: *минуту*:*второй* *часовой пояс* *год*  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Параметры  
 `date`  
 Обязательный. Дата для представления в виде строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает строковое представление даты.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `toString` метода с датой.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]