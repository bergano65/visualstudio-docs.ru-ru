---
title: метод toLocaleString (Date) | Документы Microsoft
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641354"
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Преобразует дату в строку с помощью текущего или указанного языкового стандарта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Преобразуемый объект `Date`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## <a name="remarks"></a>Примечания  
 Начиная с Internet Explorer 11 `toLocaleString` использует `Intl.DateTimeFormat` внутренним образом для сравнений убедитесь, которые добавляет поддержку для `locales` и `options` параметров. Дополнительные сведения об этих параметрах см. в разделе [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются лишь в некоторых режимах документов и версиях браузеров. Дополнительные сведения см. в разделе «Требования».  
  
 При использовании `toLocaleString` в стандартном режиме документов Internet Explorer 10, ранних версиях режимов документов и режиме совместимости:  
  
-   Он возвращает `String` , содержащий дату, записанную в длинный формат текущего языкового стандарта.  
  
-   Для дат между 1601 и 1999 г. нашей эры даты форматируется в соответствии с региональные настройки панели управления пользователя.  
  
> [!NOTE]
>  Если не указан `locales` параметра, используйте `toLocaleString` только для отображения результатов для пользователя; никогда не использовали его для вычисления значений в скриптах, так как возвращаемый результат зависит от конкретного компьютера.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toLocaleString` с заданными параметрами языкового стандарта и сравнения.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)