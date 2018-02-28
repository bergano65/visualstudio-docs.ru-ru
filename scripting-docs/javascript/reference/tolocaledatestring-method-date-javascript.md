---
title: "Метод toLocaleDateString (Date) (JavaScript) | Документы Microsoft"
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
- toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaledatestring-method-date-javascript"></a>Метод toLocaleDateString (Date) (JavaScript)
Возвращает дату в виде строкового значения, подходящего для текущего языкового стандарта среды размещения или указанного языкового стандарта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Объект `Date`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## <a name="remarks"></a>Примечания  
 Начиная с Internet Explorer 11 `toLocaleDateString` использует `Intl.DateTimeFormat` внутренним образом для форматирования даты, который обеспечивает поддержку для `locales` и `options` параметров. Дополнительные сведения об этих параметрах см. в разделе [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются лишь в некоторых режимах документов и версиях браузеров. Дополнительные сведения см. в разделе «Требования».  
  
 При использовании `toLocaleDateString` в стандартном режиме документов Internet Explorer 10, ранних версиях режимов документов и режиме совместимости:  
  
-   он возвращает строковое значение, содержащее дату в текущем часовом поясе.  
  
-   Возвращаемая дата имеет формат по умолчанию текущего языкового стандарта хост-среды.  
  
 Если параметр `locales` опустить, возвращаемое значение этого метода нельзя использовать в сценариях, поскольку оно зависит от компьютера. В этом случае метод только для форматирования отображаемого текста — никогда не при вычислении.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toLocaleDateString` с заданными параметрами языкового стандарта и сравнения.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toDateString (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)