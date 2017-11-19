---
title: "Метод toGMTString (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>Метод toGMTString (Date) (JavaScript)
Возвращает дату, преобразованную в строку с помощью Time(GMT) означает время по Гринвичу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `dateObj` ссылка представляет собой любой `Date` объекта.  
  
 `toGMTString` Метод является устаревшим и предоставляется для обеспечения обратной совместимости. Рекомендуется использовать `toUTCString` метод вместо него.  
  
 `toGMTString` Возвращает метод `String` объекта, который содержит дату в формате соглашению GMT. Возвращаемое значение имеет следующий формат: «05 Jan 1996 00:00:00 по Гринвичу.»  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toUTCString (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)