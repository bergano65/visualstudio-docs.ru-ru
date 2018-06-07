---
title: Свойство Format (Intl.NumberFormat) | Документы Microsoft
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7528c79852c4836dfd967322b876d738f9781107
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572479"
---
# <a name="format-property-intlnumberformat"></a>Свойство format (Intl.NumberFormat)
Возвращает функцию, которая форматирует число языковому стандарту, используя указанные параметры форматирования чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Параметры  
 `numberFormatObj`  
 Обязательно. Имя `NumberFormat` объект для использования в качестве модуля форматирования.  
  
## <a name="remarks"></a>Примечания  
 Функции, возвращенной методом `format` свойство принимает один аргумент, `value`и возвращает строку, представляющую число локализованных, используя параметры, указанные в `NumberFormat` объекта. Если `value` не указано, функция возвращает `NaN` (не число).  
  
## <a name="example"></a>Пример  
 В следующем примере используется `NumberFormat` объект для создания локализованных номер.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigits: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)