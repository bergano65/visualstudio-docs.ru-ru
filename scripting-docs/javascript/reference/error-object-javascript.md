---
title: "Объект Error (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Error"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Error - объект"
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Объект Error (JavaScript)
Содержит сведения об ошибках.  
  
## Синтаксис  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## Параметры  
 `errorObj`  
 Обязательный.  Имя переменной, которой присваивается объект `Error`.  Присваивание переменной опускается, если ошибка создается с помощью оператора `throw`.  
  
 `number`  
 Необязательный.  Числовое значение, присваиваемое ошибке.  Нуль, если аргумент не указан.  
  
 `description`  
 Необязательный.  Короткая строка, описывающая ошибку.  Пустая строка, если аргумент не указан.  
  
## Заметки  
 Каждый раз, когда возникает ошибка времени выполнения, для ее описания создается объект `Error`.  Этот экземпляр имеет два встроенных свойства: свойство `description` содержит описание ошибки, а свойство `number` содержит номер ошибки.  Дополнительные сведения см. в разделе [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Номер ошибки представляет собой 32\-разрядное значение.  Старшие 16 разрядов — это код устройства, а младшие разряды — фактический код ошибки.  
  
 Объекты `Error` также можно создавать явно, используя приведенный выше синтаксис, или вызывать с помощью оператора `throw`.  В обоих случаях можно добавлять любые свойства, чтобы расширить возможности объекта `Error`.  
  
 Как правило, локальная переменная, создаваемая в операторе **try...catch**, ссылается на неявно созданный объект `Error`.  Поэтому вы можете использовать номер ошибки и описание нужным вам образом.  
  
## Пример  
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
  
## Пример  
 В следующем примере показано использование неявно созданного объекта `Error`.  
  
```javascript  
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
  
## Методы  
 [Метод toString \(Error\)](../../javascript/reference/tostring-method-error.md) &#124; [Метод valueOf \(Date\)](../../javascript/reference/valueof-method-date.md)  
  
## Свойства  
 [Свойство constructor \(Error\)](../../javascript/reference/constructor-property-error.md) &#124; [Свойство description](../../javascript/reference/description-property-error-javascript.md) &#124; [Свойство message](../../javascript/reference/message-property-error-javascript.md) &#124; [Свойство name](../../javascript/reference/name-property-error-javascript.md) &#124; [Свойство number](../../javascript/reference/number-property-error-javascript.md) &#124; [Свойство prototype \(Error\)](../../javascript/reference/prototype-property-error.md) &#124; [Свойство stack \(Error\)](../../javascript/reference/stack-property-error-javascript.md) &#124; [Свойство stackTraceLimit \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Оператор var](../../javascript/reference/var-statement-javascript.md)   
 [Пример приложения Hilo на JavaScript \(Магазин Windows\)](http://hilojs.codeplex.com/SourceControl/latest)