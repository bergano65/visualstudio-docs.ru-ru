---
title: "Свойство Name (Error) (JavaScript) | Документы Microsoft"
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
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>Свойство name (Error) (JavaScript)
Возвращает имя ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Параметры  
 `errorObj`  
 Обязательный. Экземпляр `Error` объекта.  
  
## <a name="remarks"></a>Примечания  
 **Имя** свойство возвращает имя или тип исключения для ошибки. При возникновении ошибки времени выполнения, свойство имени присваивается одно из следующих типов собственных исключений:  
  
|Тип исключения|Значение|  
|--------------------|-------------|  
|ConversionError|Эта ошибка возникает при попытке преобразовать объект в формат, в который невозможно преобразовать.|  
|RangeError|Эта ошибка возникает, когда в функцию передается с аргументом, который превысил диапазона допустимых значений. Например, эта ошибка возникает при попытке создать `Array` объекта с длиной, не является допустимым положительным целым числом.|  
|ReferenceError|Эта ошибка возникает при обнаружении недопустимой ссылки. Например, эта ошибка возникает, если ожидаемая ссылка содержит `null`.|  
|RegExpError|Эта ошибка возникает, когда происходит ошибка компиляции регулярного выражения. После компиляции регулярного выражения, однако эта ошибка невозможен. В этом примере возникнет, например, если регулярное выражение объявляется с помощью шаблона, имеет недопустимый синтаксис, или с флагами, отличный от **я**, **g**, или **m**, или если она содержит флаг более одного раза.|  
|SyntaxError|Эта ошибка возникает при разборе исходного, и этот исходный текст не соблюдаются правильный синтаксис. Например, эта ошибка возникает, если `eval` функция вызывается с аргументом, который не является допустимым текстом программы.|  
|TypeError|Эта ошибка возникает, если фактический тип операнда не соответствует ожидаемому типу. При возникновении этой ошибки является примером является функция вызывается для элемента, не является объектом или не поддерживает вызов.|  
|URIError|Эта ошибка возникает при обнаружении недопустимый унифицированного указателя ресурса (URI). Например, это ошибка возникает, когда найден недопустимый символ в строке кодирования и декодирования.|  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению исключения TypeError и отображает имя и текст ошибки.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 Результат выполнения этого кода выглядит следующим образом.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство number (Error)](../../javascript/reference/number-property-error-javascript.md)