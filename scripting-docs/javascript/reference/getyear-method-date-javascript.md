---
title: "Метод getYear (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>Метод getYear (Date) (JavaScript)
Возвращает год `Date` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает год.  
  
## <a name="remarks"></a>Примечания  
  
> [!IMPORTANT]
>  Этот метод является устаревшим и предоставляется только для обратной совместимости. Вместо этого рекомендуется использовать метод `getFullYear`.  
  
 В [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], а затем в Internet Explorer версии, начиная с [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], возвращаемое значение хранимой год минус 1900. Например 1899 год возвращается как значение -1 и 2000 год возвращается как 100.  
  
 В [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] через [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], формула зависит от года. За 1900 до 1999 года значение, возвращаемое значение двузначное хранимых год минус 1900. Для даты вне этого диапазона возвращается четырехзначный год. Например 1996 возвращается как 96, но 1825 и 2025 возвращаются как есть.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Метод setYear (Date)](../../javascript/reference/setyear-method-date-javascript.md)