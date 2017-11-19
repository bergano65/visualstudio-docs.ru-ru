---
title: "Свойство Format (Intl.NumberFormat) | Документы Microsoft"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>Свойство format (Intl.NumberFormat)
Возвращает функцию, которая форматирует число языковому стандарту, используя указанные параметры форматирования чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Параметры  
 `numberFormatObj`  
 Обязательный. Имя `NumberFormat` объект для использования в качестве модуля форматирования.  
  
## <a name="remarks"></a>Примечания  
 Функции, возвращенной методом `format` свойство принимает один аргумент, `value`и возвращает строку, представляющую число локализованных, используя параметры, указанные в `NumberFormat` объекта. Если `value` не указано, функция возвращает `NaN` (не число).  
  
## <a name="example"></a>Пример  
 В следующем примере используется `NumberFormat` объект для создания локализованных номер.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)