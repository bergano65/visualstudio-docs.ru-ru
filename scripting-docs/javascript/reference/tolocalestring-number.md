---
title: "метод toLocaleString (Number) | Документы Microsoft"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Преобразует число в строку с помощью текущего или указанного языкового стандарта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Параметры  
 `numberObj`  
 Обязательный. Преобразуемый объект `Number`.  
  
 `locales`  
 Необязательно. Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта. При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом. Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательно. Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## <a name="remarks"></a>Примечания  
 Начиная с Internet Explorer 11 `toLocaleString` использует `Intl.NumberFormat` внутренним образом для сравнений убедитесь, которые добавляет поддержку для `locales` и `options` параметров. Дополнительные сведения об этих параметрах см. в разделе [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются лишь в некоторых режимах документов и версиях браузеров. Дополнительные сведения см. в разделе «Требования».  
  
> [!NOTE]
>  Если не указан `locales` параметра, используйте `toLocaleString` только для отображения результатов для пользователя; никогда не использовали его для вычисления значений в скриптах, так как возвращаемый результат зависит от конкретной машины (метод возвращает текущий языковой стандарт).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `toLocaleString` метод без параметров.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toLocaleString` с заданными параметрами языкового стандарта и сравнения.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)