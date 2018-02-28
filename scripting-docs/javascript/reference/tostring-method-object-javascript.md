---
title: "Метод toString (Object) (JavaScript) | Документы Microsoft"
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
- toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>Метод toString (Object) (JavaScript)
Возвращает строковое представление объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Параметры  
 `objectname`  
 Обязательный. Объект, для которого ищется строковое представление.  
  
 `radix`  
 Необязательно. Указывает основание для преобразования числовых значений в строки. Это значение используется только для чисел.  
  
## <a name="remarks"></a>Примечания  
 **ToString** метод входит в состав все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов. Его поведение зависит от типа объекта.  
  
|Объект|Поведение|  
|------------|--------------|  
|Массив|Элементы `Array` преобразуются в строки. Результирующие строки объединяются, разделенных запятыми.|  
|Boolean|Если логическое значение — **true**, возвращает «`true`». В противном случае возвращает "`false`«.|  
|Дата|Возвращает текстовое представление даты.|  
|Ошибка|Возвращает строку, содержащую сообщение об ошибке.|  
|Функция|Возвращает строку следующего вида, где *functionname* имя функции, **toString** был вызван метод:<br /><br /> `function functionname( ) { [native code] }`|  
|Число|Возвращает текстовое представление числа.|  
|Строка|Возвращает значение `String` объекта.|  
|По умолчанию|Возвращает `"[object objectname]"`, где `objectname` имя типа объекта.|  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **toString** метода с аргументом основание системы счисления. Возвращаемое значение функции, показано ниже является таблицей преобразования основание системы счисления.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Применяется к**: [объект Array](../../javascript/reference/array-object-javascript.md)&#124; [Логический объект](../../javascript/reference/boolean-object-javascript.md)&#124; [Дата объекта](../../javascript/reference/date-object-javascript.md)&#124; [Объекта error](../../javascript/reference/error-object-javascript.md)&#124; [Функции объекта](../../javascript/reference/function-object-javascript.md)&#124; [Номер объекта](../../javascript/reference/number-object-javascript.md)&#124; [Объекта](../../javascript/reference/object-object-javascript.md)&#124; [Строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)