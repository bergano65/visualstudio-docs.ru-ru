---
title: "Сведения о версии JavaScript | Документы Microsoft"
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
helpviewer_keywords: JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: "93"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0503abb3d62e9fd61149b884a7b58a685fbc62c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-version-information"></a>Сведения о версии JavaScript
Разные версии JavaScript поддерживают разные наборы элементов JavaScript. Набор функций, поддерживаемых приложениями[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , несколько отличается от набора функций Internet Explorer.  
  
> [!IMPORTANT]
>  Приложения [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] представляют собой новый тип приложений, запускаемых на устройствах с [!INCLUDE[win8](../../javascript/includes/win8-md.md)] . Дополнительные сведения о приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] см. в разделе [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 Поддерживаемый набор элементов стандартного режима (используемого во всех версиях Internet Explorer вплоть до Internet Explorer 11 при наличии директивы `<!doctype>` ) отличается от набора элементов, поддерживаемого в режиме совместимости (используемом при отсутствии директивы `<!doctype>` ). Дополнительные сведения об управлении версиями см. в разделе [Определение совместимости документов](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 В следующей таблице показаны режимы документов Internet Explorer (и приложений Магазина, представляющих [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] и [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]), поддерживающих определенные элементы языка. Если режимы документов поддерживают указанный элемент, они отображаются с буквой **Y**, если нет — с буквой **N**.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (браузер Edge в Windows 10) не включает поддержку устаревших режимов документов. Приложения [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] поддерживаются начиная с Windows Phone 8.1. Экспериментальные функции (о: flags) обозначаются «Exp».  
  
 Таблица содержит сводную информацию. Более подробные сведения см. в документации по элементам языка.  
  
|Элемент языка|Режим совместимости, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7|Стандартный режим Internet Explorer 8|Стандартный режим Internet Explorer 9|Стандартный режим Internet Explorer 10|Стандартный режим Internet Explorer 11|Пограничный случай|Приложения Магазина|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ свойство (Object)](../../javascript/reference/proto-property-object-javascript.md)|в|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Свойства $1...$9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство 0n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция abs](../../javascript/reference/math-abs-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция acos](../../javascript/reference/math-acos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция acosh](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Объект ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Оператор присваивания сложения (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор сложения (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод apply](../../javascript/reference/apply-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект arguments](../../javascript/reference/arguments-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство arguments](../../javascript/reference/arguments-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Array](../../javascript/reference/array-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция Array.from (Array)](../../javascript/reference/array-from-function-array-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Функция Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|в|N|Y|Y|Y|Y|Y|  
|[Функция Array.of (Array)](../../javascript/reference/array-of-function-array-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)|в|N|N|Y|Y|Y|Y|  
|[Функции](../../javascript/functions-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Функция asin](../../javascript/reference/math-asin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция Object.assign (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Оператор присваивания (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция atan](../../javascript/reference/math-atan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция atan2](../../javascript/reference/math-atan2-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод atEnd](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Метод bind](../../javascript/reference/bind-method-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Оператор присваивания побитового И (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор побитового И (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор побитового НЕ (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Побитовое или оператор присваивания (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Побитовый оператор или оператор (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания побитового исключающего ИЛИ (^=)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор побитового исключающего ИЛИ (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод blink](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод bold](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Boolean](../../javascript/reference/boolean-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор break](../../javascript/reference/break-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод call](../../javascript/reference/call-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство callee](../../javascript/reference/callee-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство caller](../../javascript/reference/caller-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция ceil](../../javascript/reference/math-ceil-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод charAt](../../javascript/reference/charat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор class](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Метод codePointAt (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор "запятая" (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[// (оператор однострочного комментария)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[/*.. \*/ (Оператор многострочного комментария)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Операторы сравнения](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод compile](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод concat (массив)](../../javascript/reference/concat-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод concat (строка)](../../javascript/reference/concat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[Условный (троичный) оператор (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство сonstructor](../../javascript/reference/constructor-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор const](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Оператор continue](../../javascript/reference/continue-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция cos](../../javascript/reference/math-cos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция create](../../javascript/reference/object-create-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Объект DataView](../../javascript/reference/dataview-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Date](../../javascript/reference/date-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Debug](../../javascript/reference/debug-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|в|N|N|Y|Y|Y|Y|  
|[Свойство Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|в|N|N|Y|Y|Y|Y|  
|[Оператор debugger](../../javascript/reference/debugger-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор декремента (--)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функции](../../javascript/functions-javascript.md)|в|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Функция defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Функция defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Оператор delete](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство description](../../javascript/reference/description-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания деления (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор деления (/)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод entries (Array)](../../javascript/reference/entries-method-array-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)|Y|Y|Y|Y|Y|Y|в|  
|[Константы Number](../../javascript/reference/number-constants-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Оператор равенства (==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Error](../../javascript/reference/error-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство stack (Error)](../../javascript/reference/stack-property-error-javascript.md)|в|N|N|Y|Y|Y|Y|  
|[Свойство stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|в|N|N|Y|Y|Y|Y|  
|[Функция escape](../../javascript/reference/escape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция eval](../../javascript/reference/eval-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод exec](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод every](../../javascript/reference/every-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция exp](../../javascript/reference/math-exp-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод fill (Array)](../../javascript/reference/fill-method-array-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Метод filter](../../javascript/reference/filter-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Оператор finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод findIndex (Array)](../../javascript/reference/findindex-method-array-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Метод fixed](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Float32Array](../../javascript/reference/float32array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Float64Array](../../javascript/reference/float64array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Функция floor](../../javascript/reference/math-floor-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор for](../../javascript/reference/for-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод forEach](../../javascript/reference/foreach-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор for...of](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|в|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Функция freeze](../../javascript/reference/object-freeze-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Объект Function](../../javascript/reference/function-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор function](../../javascript/reference/function-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Генераторы](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Метод getDate](../../javascript/reference/getdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getDay](../../javascript/reference/getday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getHours](../../javascript/reference/gethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getItem](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция GetObject](../../javascript/reference/getobject-function-javascript.md)|Y|Y|N|N|N|N|N|  
|[Функция getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Функция getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getTime](../../javascript/reference/gettime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Метод getYear](../../javascript/reference/getyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Global](../../javascript/reference/global-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство global](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор "больше чем" (>)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор "больше чем или равно" (>=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Методы HTML-тегов](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция hypot](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор тождества (===)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция imul](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор In](../../javascript/reference/in-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод includes (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор инкремента (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство index](../../javascript/reference/index-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод indexOf (массив)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод indexOf (строка)](../../javascript/reference/indexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор неравенства (!=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа Infinity](../../javascript/reference/infinity-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство input ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор instanceof](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Int8Array](../../javascript/reference/int8array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Int16Array](../../javascript/reference/int16array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Int32Array](../../javascript/reference/int32array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)|в|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)|в|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)|в|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Функция isFinite](../../javascript/reference/isfinite-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция IsExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Функция isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Функция isNaN](../../javascript/reference/isnan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция isNaN (число)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Формат даты ISO](../../javascript/date-and-time-strings-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод IsPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция isSealed](../../javascript/reference/object-issealed-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод italics](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Итераторы](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод item](../../javascript/reference/item-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод join](../../javascript/reference/join-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект JSON](../../javascript/reference/json-object-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Функция keys](../../javascript/reference/object-keys-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод keys (Array)](../../javascript/reference/keys-method-array-javascript.md)|в|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор с меткой](../../javascript/reference/labeled-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод lastIndexOf (массив)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод lastIndexOf (строка)](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство lastMatch ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство lastParen ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод lbound](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство leftContext ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания сдвига влево (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство length (аргументы)](../../javascript/reference/length-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство length (массив)](../../javascript/reference/length-property-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство length (функция)](../../javascript/reference/length-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство length (строка)](../../javascript/reference/length-property-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор "меньше чем" (<)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор "меньше чем или равно" (<=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор let](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Метод link](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа LN2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа LN10](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция log](../../javascript/reference/math-log-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа LOG2E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа LOG10E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор логического И (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор логического НЕ (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Логическое или оператор (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод map](../../javascript/reference/map-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Объект Map](../../javascript/reference/map-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Метод match](../../javascript/reference/match-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Math](../../javascript/reference/math-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция max](../../javascript/reference/math-max-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа MAX_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство message](../../javascript/reference/message-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция min](../../javascript/reference/math-min-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа MIN_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания модуля (%=)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор модуля (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания умножения (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор умножения (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство name](../../javascript/reference/name-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа NaN (глобальная)](../../javascript/reference/nan-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа NaN (число)](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор нетождества (!==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция now](../../javascript/reference/date-now-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Объект Number](../../javascript/reference/number-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство number](../../javascript/reference/number-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Object](../../javascript/reference/object-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Функция parseFloat](../../javascript/reference/parsefloat-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция parseInt](../../javascript/reference/parseint-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа PI](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод pop](../../javascript/reference/pop-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция pow](../../javascript/reference/math-pow-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Объект Promise](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Свойство prototype](../../javascript/reference/prototype-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Прокси-объект](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод push](../../javascript/reference/push-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция random](../../javascript/reference/math-random-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция raw](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод reduce](../../javascript/reference/reduce-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Объект RegExp](../../javascript/reference/regexp-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Синтаксис регулярного выражения](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|Y|Y|Y|Y|Y|Y|  
|[Флаг регулярного выражения /y](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Метод repeat (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод replace](../../javascript/reference/replace-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функции](../../javascript/functions-javascript.md)|в|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Оператор return](../../javascript/reference/return-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод reverse](../../javascript/reference/reverse-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство rightContext ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания сдвига вправо (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция round](../../javascript/reference/math-round-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция seal](../../javascript/reference/object-seal-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод search](../../javascript/reference/search-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Set](../../javascript/reference/set-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Метод setDate](../../javascript/reference/setdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|Y|Y|Y|Y|Y|  
|[Метод setHours](../../javascript/reference/sethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setTime](../../javascript/reference/settime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод setYear](../../javascript/reference/setyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод shift](../../javascript/reference/shift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция sin](../../javascript/reference/math-sin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод slice (массив)](../../javascript/reference/slice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод slice (строка)](../../javascript/reference/slice-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод small](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод some](../../javascript/reference/some-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод sort](../../javascript/reference/sort-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Свойство source](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод splice](../../javascript/reference/splice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод split](../../javascript/reference/split-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функции](../../javascript/functions-javascript.md)|в|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Функция sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа SQRT1_2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа SQRT2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Директива use strict](../../javascript/reference/use-strict-directive.md)|в|N|N|Y|Y|Y|Y|  
|[Метод strike](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект String](../../javascript/reference/string-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Метод sub](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод substr](../../javascript/reference/substr-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод substring](../../javascript/reference/substring-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания вычитания (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор вычитания (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод sup](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор switch](../../javascript/reference/switch-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Symbol](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Функция tan](../../javascript/reference/math-tan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Строки шаблона](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод test](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор this](../../javascript/reference/this-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор throw](../../javascript/reference/throw-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toArray](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Метод toJSON](../../javascript/reference/tojson-method-date-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Метод toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toLocaleLowercase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toLocaleUppercase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toString](../../javascript/reference/tostring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод trim](../../javascript/reference/trim-method-string-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Оператор try](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект Uint8Array](../../javascript/reference/uint8array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Uint16Array](../../javascript/reference/uint16array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Uint32Array](../../javascript/reference/uint32array-object.md)|в|N|N|Y|Y|Y|Y|  
|[Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)|в|N|N|N|Y|Y|v8: N<br />v8.1 (Win): Y<br />v8.1 (Phone): No<br />v10: Y|  
|[Оператор унарного отрицания (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Константа undefined](../../javascript/reference/undefined-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция unescape](../../javascript/reference/unescape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Escape-символы для кодовых точек Юникода](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Метод unshift](../../javascript/reference/unshift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор присваивания сдвига вправо без учета знака (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Директива use strict](../../javascript/reference/use-strict-directive.md)|в|N|N|Y|Y|Y|Y|  
|[Функция UTC](../../javascript/reference/date-utc-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Метод values (Array)](../../javascript/reference/values-method-array-javascript.md)|в|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор var](../../javascript/reference/var-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Оператор void](../../javascript/reference/void-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект WeakMap](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Объект WeakSet](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Оператор while](../../javascript/reference/while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Объект WinRTError](../../javascript/reference/winrterror-object-javascript.md)|в|N|N|Y|Y|Y|Y|  
|[Оператор with](../../javascript/reference/with-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция write](../../javascript/reference/debug-write-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Функция writeln](../../javascript/reference/debug-writeln-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
  
 \*Поддерживает объекты DOM, но не пользовательские объекты. Атрибуты `enumerable` и `configurable` можно указать, но они не используются.  
  
## <a name="see-also"></a>См. также  
 [Определение совместимости документов](http://go.microsoft.com/fwlink/?LinkId=208537)