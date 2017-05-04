---
title: "Свойство name (Error) (JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name - свойство"
  - "name - свойство, имя ошибки"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Свойство name (Error) (JavaScript)
Возвращает имя ошибки.  
  
## Синтаксис  
  
```  
  
errorObj.  
name  
  
```  
  
## Параметры  
 `errorObj`  
 Обязательный.  Экземпляр объекта `Error`.  
  
## Заметки  
 Свойство **name** возвращает имя или тип исключения для ошибки.  При возникновении ошибки времени выполнения для свойства "name" устанавливается один из собственных типов исключений, перечисленных ниже.  
  
|Тип исключения|Значение|  
|--------------------|--------------|  
|ConversionError|Данная ошибка возникает при попытке преобразовать объект в тип, в который он не может быть преобразован.|  
|RangeError|Данная ошибка возникает, если функции передается аргумент, значение которого находится за пределами диапазона допустимых значений.  Например, эта ошибка возникает при попытке создания объекта `Array` с длиной, которая не является допустимым положительным целым числом.|  
|ReferenceError|Данная ошибка возникает при обнаружении недопустимой ссылки.  Данная ошибка возникает, например, если ожидаемая ссылка имеет значение `null`.|  
|RegExpError|Данная ошибка возникает в случае ошибки компиляции регулярного выражения.  Однако после компиляции регулярного выражения эта ошибка произойти не может.  Эта ошибка возникает, например, если регулярное выражение объявляется с шаблоном, имеющим недопустимый синтаксис, или с флагами, отличными от **i**, **g** и **m**, либо если в нем имеется один и тот же флаг, повторяющийся несколько раз.|  
|SyntaxError|Данная ошибка возникает при синтаксическом анализе исходного текста, если синтаксис этого текста неверен.  Например, эта ошибка возникает, если функция `eval` вызывается с аргументом, который не является допустимым текстом программы.|  
|TypeError|Данная ошибка возникает, если фактический тип операнда не соответствует ожидаемому типу.  Такая ситуация возникает, например, если вызов функции выполнен для чего\-то, что не является объектом или не поддерживает вызов.|  
|URIError|Данная ошибка возникает при обнаружении недопустимого URI \(Uniform Resource Indicator — унифицированный указатель ресурса\).  Например, такая ошибка возникает при обнаружении в кодируемой или декодируемой строке недопустимого символа.|  
  
## Пример  
 В следующем примере создается исключение TypeError, отображаются имя ошибки и соответствующее ей сообщение.  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Пример  
 Результат выполнения этого кода следующий.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство number \(Error\)](../../javascript/reference/number-property-error-javascript.md)