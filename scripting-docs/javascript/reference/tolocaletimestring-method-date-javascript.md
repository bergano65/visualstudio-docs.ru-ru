---
title: "Метод toLocaleTimeString (Date) (JavaScript) | Документы Microsoft"
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
- toLocaleTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleTimeString method
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77d8ee8fb6757b13da22a3cf3a59d28a105292cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaletimestring-method-date-javascript"></a>Метод toLocaleTimeString (Date) (JavaScript)
Возвращает время в виде строкового значения, подходящего для текущего языкового стандарта среды размещения или указанного языкового стандарта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Объект `Date`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## <a name="remarks"></a>Примечания  
 Начиная с Internet Explorer 11 `toLocaleTimeString` использует `Intl.DateTimeFormat` внутренним образом для форматирования времени, что добавляет поддержку параметров `locales` и `options`. Дополнительные сведения об этих параметрах см. в разделе [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются лишь в некоторых режимах документов и версиях браузеров. Дополнительные сведения см. в разделе «Требования».  
  
 При использовании `toLocaleTimeString` в стандартном режиме документов Internet Explorer 10, ранних версиях режимов документов и режиме совместимости:  
  
-   Он возвращает строковое значение, содержащее время в текущем часовом поясе.  
  
-   Возвращаемое значение времени указано в формате по умолчанию для текущего языкового стандарта среды размещения.  
  
 Если параметр `locales` опустить, возвращаемое значение этого метода нельзя использовать в сценариях, поскольку оно зависит от компьютера. В этом случае метод только для форматирования отображаемого текста — никогда не при вычислении.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toLocaleTimeString` с заданными параметрами языкового стандарта и сравнения.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toTimeString (Date)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [Метод toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)