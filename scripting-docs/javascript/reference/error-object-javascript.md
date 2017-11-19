---
title: "Объект Error (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="error-object-javascript"></a>Объект Error (JavaScript)
Содержит сведения об ошибках.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Параметры  
 `errorObj`  
 Обязательный. Имя переменной, которой присваивается объект `Error`. Присваивание переменной опускается, если ошибка создается с помощью оператора `throw`.  
  
 `number`  
 Необязательно. Числовое значение, присваиваемое ошибке. Нуль, если аргумент не указан.  
  
 `description`  
 Необязательно. Короткая строка, описывающая ошибку. Пустая строка, если аргумент не указан.  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда возникает ошибка времени выполнения, для ее описания создается объект `Error`. Этот экземпляр имеет два встроенных свойства: свойство `description` содержит описание ошибки, а свойство `number` содержит номер ошибки. Дополнительные сведения см. в разделе [ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Номер ошибки представляет собой 32-разрядное значение. Старшие 16 разрядов — это код устройства, а младшие разряды — фактический код ошибки.  
  
 Объекты `Error` также можно создавать явно, используя приведенный выше синтаксис, или вызывать с помощью оператора `throw`. В обоих случаях можно добавлять любые свойства, чтобы расширить возможности объекта `Error`.  
  
 Как правило, локальная переменная, созданная в **try... catch** Инструкция ссылается на неявно созданный `Error` объекта. Поэтому вы можете использовать номер ошибки и описание нужным вам образом.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование объекта `Error`.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование неявно созданного объекта `Error`.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Методы  
 [Метод toString (Error)](../../javascript/reference/tostring-method-error.md) &#124; [метод valueOf (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Свойства  
 [Свойство constructor (Error)](../../javascript/reference/constructor-property-error.md) &#124; [свойство description](../../javascript/reference/description-property-error-javascript.md) &#124; [свойство message](../../javascript/reference/message-property-error-javascript.md) &#124; [свойство name](../../javascript/reference/name-property-error-javascript.md) &#124; [свойство number](../../javascript/reference/number-property-error-javascript.md) &#124; [свойство prototype (Error)](../../javascript/reference/prototype-property-error.md) &#124; [свойство stack (Error)](../../javascript/reference/stack-property-error-javascript.md) &#124; [свойство stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Try... catch... finally инструкции](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Оператор var](../../javascript/reference/var-statement-javascript.md)   
 [Пример приложения Hilo JavaScript (магазин Windows)](http://hilojs.codeplex.com/SourceControl/latest)