---
title: "Метод setYear (Date) (JavaScript) | Документы Microsoft"
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
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>Метод setYear (Date) (JavaScript)
Устанавливает значение года `Date` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numYear`  
 Обязательный. За 1900 до 1999 года это числовое значение, представляющее год минус 1900. Даты вне этого диапазона это 4-значное числовое значение.  
  
## <a name="remarks"></a>Примечания  
 Этот метод является устаревшим и сохраняется для обеспечения обратной совместимости. Вместо этого рекомендуется использовать метод `setFullYear`.  
  
 Чтобы задать год `Date` объекта 1997, вызов **setYear(97)**. Чтобы установить 2010 год, вызовите **setYear(2010)**. Наконец, чтобы задать года год в диапазоне от 0 до 99, используйте `setFullYear` метод.  
  
> [!NOTE]
>  Для [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] версии 1.0, `setYear` использует значение, которое является результатом сложения 1900 для значения года, полученного от `numYear`, независимо от значения года. Например, чтобы установить 1899 года `numYear` равно -1 и задать 2000 года `numYear` равно 100.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод getYear (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)