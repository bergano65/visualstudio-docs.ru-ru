---
title: "Объект Intl.NumberFormat (JavaScript) | Документы Microsoft"
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
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Объект Intl.NumberFormat (JavaScript)
Обеспечивает формат чисел, соответствующий языковому стандарту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Параметры  
 `numberFormatObj`  
 Обязательный. Имя переменной, которой нужно присвоить объект `NumberFormat`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript. Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательно. Объект, который содержит один или несколько свойств, определяющих форматов чисел. Подробные сведения см. в разделе "Заметки".  
  
## <a name="remarks"></a>Примечания  
 `locales` Параметр должен соответствовать [BCP-47](http://tools.ietf.org/html/rfc5646) тегов языка или языкового стандарта, например «en US» и «zh-CN». Тег может включать язык, регион, страну и вариант. Примеры тегов языка см. в разделе [приложение A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Для `NumberFormat`, вы можете добавить **-u** подтег следуют - Чис указать нумерации расширение системы:  
  
 «*язык*-*область*-u-Чис -*numberingsystem*»  
  
 где *numberingsystem* может принимать одно из следующих: арабские, arabext, bali, beng, deva, fullwide, gujr, технике, hanidec, khmr, knda, laoo, latn, жизни, mylm, mong, mymr, orya, tamldec, telu, тайский, tibt.  
  
 Параметр `options` может содержать указанные ниже свойства.  
  
|Свойство|Описание|Возможные значения|Значение по умолчанию|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Задает используемый алгоритм подбора языкового стандарта.|«Просмотр», «оптимальных параметров»|"best fit"|  
|`style`|Указывает стиль формат числа.|«decimal», «процент», «currency»|«десятичное число»|  
|`currency`|Указывает значение валюты в формате ISO 4217 как буквенный код. Если `style` имеет значение на «currency», это значение является обязательным.|В разделе ISO [валют и фондов кода списка](http://www.currency-iso.org/en/home/tables/table-a1.html).|Не определено|  
|`currencyDisplay`|Включение отображения валюты код валюты по алфавиту в формате ISO 4217, символ валюты, локализованное или валюты локализованное имя. Это значение используется только в том случае, если `style` имеет значение «валюта».|«код», «символ», «имя»|«символ»|  
|`useGrouping`|Указывает, следует ли использовать разделитель групп.|значение true, false|`true`.|  
|`minimumIntegerDigits`|Указывает минимальное число цифр целой части для использования.|1 по 21.|21|  
|`minimumFractionDigits`|. Указывает минимальное число цифр дробной части для использования.|0 до 20.|0|  
|`maximumFractionDigits`|Указывает максимальное количество цифр дробной части для использования.|Это значение может изменяться от `minimumFractionDigits` до 20 символов.|20.|  
|`minimumSignificantDigits`|Указывает минимальное число цифр дробной части, который будет отображаться.|Это значение находится в диапазоне от 1 до 21.|1|  
|`maximumSignificantDigits`|Указывает максимальное количество цифр дробной части, который будет отображаться.|Это значение может изменяться от `minimumSignificantDigits` 21.|21|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `NumberFormat`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[Конструктор](../../javascript/reference/constructor-property-intl-numberformat.md)|Указывает функцию, которая создает пустой объект модуля форматирования.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Возвращает функцию, в котором число форматируется с помощью параметров форматирования чисел.|  
|[прототип](../../javascript/reference/prototype-property-intl-numberformat.md)|Возвращает ссылку на прототип для модуля форматирования чисел.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `NumberFormat`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Возвращает объект, содержащий свойства и значения объекта средства форматирования.|  
  
## <a name="example"></a>Пример  
 В следующем примере создается `NumberFormat` объект для языка "en US" с указанными параметрами форматирования.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>Пример  
 В следующих примерах результат с помощью несколько разных языков и параметров.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [метод toLocaleString (Number)](../../javascript/reference/tolocalestring-number.md)   
 [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)