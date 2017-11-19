---
title: "Объект Intl.DateTimeFormat (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Объект Intl.DateTimeFormat (JavaScript)
Обеспечивает форматирование даты и времени, соответствующее языковому стандарту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Параметры  
 `dateTimeFormatObj`  
 Обязательный. Имя переменной, которой нужно присвоить объект `DateTimeFormat`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript. Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры форматирования даты и времени. Подробные сведения см. в разделе "Заметки".  
  
## <a name="remarks"></a>Примечания  
 `locales` Параметр должен соответствовать [BCP-47](http://tools.ietf.org/html/rfc5646) тегов языка или языкового стандарта, например «en US» и «zh-CN». Тег может включать язык, регион, страну и вариант. Примеры тегов языка см. в разделе [приложение A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Для `DateTimeFormat`, вы можете добавить **-u** подтег в строке языкового стандарта, чтобы включить один или оба из следующих расширений Юникода:  
  
-   -Чис указать нумерации расширение системы: *язык*-*область*-u-Чис -*numberingsystem*  
  
     где *numberingsystem* может принимать одно из следующих: арабские, arabext, bali, beng, deva, fullwide, gujr, технике, hanidec, khmr, knda, laoo, latn, жизни, mylm, mong, mymr, orya, tamldec, telu, тайский, tibt.  
  
-   -ЦС, чтобы указать календарь: *язык*-*область*-u-ЦС -*календаря*  
  
     где *календаря* может принимать одно из следующих: буддистский, китайский, Грегори, Исламская, islamicc, японский.  
  
 Параметр `options` может содержать указанные ниже свойства.  
  
|Свойство|Описание|Возможные значения|Значение по умолчанию|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Задает используемый алгоритм подбора языкового стандарта.|"lookup","best fit"|"best fit"|  
|`formatMatcher`|Задает используемый алгоритм подбора формата.|"basic", "best fit"|"best fit"|  
|`hour12`|Указывает, использовать ли для часов 12-часовой формат.|`true` (для 12-часового формата), `false` (для 24-часового формата)||  
|`timeZone`|Задает часовой пояс. Как минимум, всегда поддерживается "UTC".|Значение часового пояса, например "UTC".|"UTC"|  
|`weekday`|Задает форматирование дня недели.|"narrow", "short", "long"|Не определено|  
|`era`|Задает форматирование эры.|"narrow", "short", "long"|Не определено|  
|`year`|Задает форматирование года.|"2-digit", "numeric"|Не определено или "numeric"|  
|`month`|Задает форматирование месяца.|"2-digit", "numeric", "narrow", "short", "long"|Не определено или "numeric"|  
|`day`|Задает форматирование дня.|"2-digit", "numeric"|Не определено или "numeric"|  
|`hour`|Задает форматирование часов.|"2-digit", "numeric"|Не определено|  
|`minute`|Задает форматирование минут.|"2-digit", "numeric"|Не определено|  
|`second`|Задает форматирование секунд.|"2-digit", "numeric"|Не определено|  
|`timeZoneName`|Задает форматирование часового пояса. Данное свойство в настоящий момент не поддерживается.|"short", "long"|Данное свойство в настоящий момент не поддерживается.|  
  
 Значения по умолчанию для свойств `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` и `second` — `undefined`. Если эти свойства не заданы, для свойств `year`, `month` и `day` используется форматирование типа "numeric".  
  
 Все языковые стандарты должны поддерживать по крайней мере следующие форматы:  
  
-   день недели, год, месяц, день, час, минута, секунда;  
  
-   день недели, год, месяц, день;  
  
-   год, месяц, день;  
  
-   год, месяц;  
  
-   месяц, день;  
  
-   час, минута, секунда;  
  
-   час, минута.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `DateTimeFormat`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[Конструктор](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Указывает функцию, создающую объект средства форматирования даты и времени.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Возвращает функцию, которая форматирует дату, соответствующую языковому стандарту, используя параметры средства форматирования даты и времени.|  
|[прототип](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Возвращает ссылку на прототип для средства форматирования даты и времени.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `DateTimeFormat`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Возвращает объект, содержащий свойства и значения объекта средства форматирования даты и времени.|  
  
## <a name="example"></a>Пример  
 В следующем примере показан результат передачи объекта Date в объект `DateTimeFormat` с использованием различных языковых стандартов.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере создается объект `DateTimeFormat`, задающий текущий день недели в длинном формате с использованием языкового стандарта "Арабский (Саудовская Аравия)", исламского календаря и латинской системы нумерации.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [метод toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [Метод toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)