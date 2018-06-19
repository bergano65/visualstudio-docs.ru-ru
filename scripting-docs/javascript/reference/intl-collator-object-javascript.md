---
title: Объект Intl.Collator (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640004"
---
# <a name="intlcollator-object-javascript"></a>Объект Intl.Collator (JavaScript)
Обеспечивает сравнение строк, соответствующее языковому стандарту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Параметры  
 `collatorObj`  
 Обязательный. Имя переменной, которой нужно присвоить объект `Collator`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript. Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения. Подробные сведения см. в разделе "Заметки".  
  
## <a name="remarks"></a>Примечания  
 `locales` Параметр должен соответствовать [BCP-47](http://tools.ietf.org/html/rfc5646) тегов языка или языкового стандарта, например «en US» и «Hans-zh-CN». Тег может включать язык, регион, страну и вариант. Список языков см. в разделе [IANA языка подтег реестра](http://go.microsoft.com/fwlink/p/?linkid=227303). Примеры тегов языка см. в разделе [приложение A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Для `Collator`, вы можете включить расширение -u в строке языкового стандарта, чтобы указать один или несколько из следующих расширений Юникода:  
  
-   -co, чтобы задать параметры сортировки, variant (языкового стандарта): "*язык*-*область*-u-co -*значение*».  
  
-   -kn для указания числового сравнения: "*языка*-*область*- u kn значение true &#124; false».  
  
-   -kf укажите, следует ли сначала сортировки символов верхнего или нижнего: «*язык*-*область*- u kf верхней &#124; нижнего &#124; false»). Это расширение в настоящее время не поддерживается.  
  
 Чтобы указать числового сравнения, можно задать расширение -kn в строке языкового стандарта или использовать `numeric` свойства `options` параметра. Если вы используете `numeric` - kn значение свойства, не применяется.  
  
 Параметр `options` может содержать указанные ниже свойства.  
  
-   `localeMatcher`. Задает используемый алгоритм подбора языкового стандарта. Возможные значения: «Уточняющий запрос» и «оптимальных параметров». Значение по умолчанию — «наилучшее соответствие».  
  
-   `usage`. Определяет сортировку или поиск цели сравнения. Возможные значения: «сортировка» и «поиск». Значение по умолчанию — «сортировка».  
  
-   `sensitivity`. Указывает чувствительность средства упорядочивания. Возможными значениями являются «базовый», «диакритических знаков», «регистр» и «variant». Значение по умолчанию — `undefined`.  
  
-   `ignorePunctuation`. Указывает, следует ли игнорировать знаков препинания в сравнении. Возможными значениями являются «true» и «false». Значение по умолчанию — `false`.  
  
-   `numeric`. Указывает, используется ли числовые сортировки. Возможными значениями являются «true» и «false». Значение по умолчанию — `false`.  
  
-   `caseFirst`. В настоящее время не поддерживается.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Collator`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Возвращает функцию, которая сравнивает две строки с помощью средства упорядочивания порядок сортировки.|  
|[Конструктор](../../javascript/reference/constructor-property-intl-collator.md)|Указывает функцию, которая создает средства упорядочивания.|  
|[прототип](../../javascript/reference/prototype-property-intl-collator.md)|Возвращает ссылку на прототип для средства упорядочивания.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Collator`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Возвращает объект, содержащий свойства и значения средства упорядочивания.|  
  
## <a name="example"></a>Пример  
 В следующем примере создается `Collator` объекта и выполняет сравнение.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере используется `Collator` объекты для сортировки массива. В этом примере показаны различия определенного языкового стандарта.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере используется `Collator` для поиска строки и указывает параметры сравнения.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод localeCompare (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)