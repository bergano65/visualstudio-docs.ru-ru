---
title: "Метод localeCompare (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="localecompare-method-string-javascript"></a>Метод localeCompare (String) (JavaScript)
Определяет, эквивалентны ли две строки в текущем языковом стандарте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Параметры  
 `stringVar`  
 Обязательный. Первая сравниваемая строка.  
  
 `stringExp`  
 Обязательный. Вторая сравниваемая строка.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript. Этот параметр должен соответствовать [BCP-47](http://tools.ietf.org/html/rfc5646) стандартов см. в разделе [объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) подробные сведения.  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения. в разделе [объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) подробные сведения.  
  
## <a name="remarks"></a>Примечания  
 Для сравнения строк, можно указать либо `String` объектов или строковых литералов.  
  
 Начиная с Internet Explorer 11 `localeCompare` использует `Intl.Collator` внутренне объект для сравнения, который добавляет поддержку для `locales` и `options` параметров. Дополнительные сведения об этих параметрах см. в разделе [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) и [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются лишь в некоторых режимах документов и версиях браузеров. Дополнительные сведения см. в разделе «Требования».  
  
 `localeCompare` Метод выполняет сравнение строк с учетом языкового стандарта `stringVar` и `stringExp` и возвращает одно из следующих результатов, в зависимости от порядка сортировки по умолчанию:  
  
-   -1, если `stringVar` предшествует `stringExp`.  
  
-   + 1, если `stringVar` сортируется после `stringExp`.  
  
-   0 (нуль), если две строки являются эквивалентными.  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `localeCompare`.  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Пример  
 Следующий код показывает, как использовать `localeCompare` с языковым стандартом, немецкий (Германия).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `localeCompare` с немецкий (Германия) языка и языкового стандарта расширение, которое указывает порядок сортировки для немецкого телефонной книги. В этом примере показаны различия определенного языкового стандарта.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleString (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)