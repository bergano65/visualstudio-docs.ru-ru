---
title: Try... catch... finally (JavaScript) оператор | Документы Microsoft
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
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641734"
---
# <a name="trycatchfinally-statement-javascript"></a>Оператор try...catch...finally (JavaScript)
Настраивает блоки кода, в которых ошибки, возникшие в одном блоке, обрабатываются в другом. Ошибки, возникающие внутри блока `try`, перехватываются в блоке `catch`. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## <a name="parameters"></a>Параметры  
 `tryStatements`  
 Обязательный. Операторы, в которых может возникнуть ошибка.  
  
 `exception`  
 Обязательный. Любое имя переменной. Начальное значение `exception` — это значение возникшей ошибки.  
  
 `catchStatements`  
 Необязательно. Операторы обработки ошибок, возникающих в соответствующем блоке `tryStatements`.  
  
 `finallyStatements`  
 Необязательно. Операторы, безусловно выполняемые после выполнения всех остальных действий по обработке ошибки.  
  
## <a name="remarks"></a>Примечания  
 Оператор `try...catch...finally` позволяет обрабатывать некоторые или все ошибки, которые могут возникать в конкретном блоке кода, не прерывая выполнения кода,. Если возникают ошибки, которые не обрабатываются, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] предоставляет обычное сообщение об ошибке.  
  
 Блок `try` содержит код, который может спровоцировать ошибку, а блок `catch` — код, который обрабатывает некоторые или все ошибки. Если в блоке `try` возникает ошибка, управление программой передается блоку `catch`. Значение `exception` — это значение ошибки, возникшей в блоке `try`. Если ошибок нет, блок `catch` не выполняется.  
  
 Можно передать ошибку на следующий уровень с помощью оператора `throw` для повторного создания ошибки.  
  
 После того как в блоке `try` выполнены все операторы и в блоке `catch` обработаны все ошибки, выполняются операторы в блоке `finally` (независимо от того, была ли обработана ошибка). Код в `finally` блок выполняется всегда, если не произошла необработанная ошибка (например, ошибка времени выполнения внутри **перехватывать** блока).  
  
## <a name="example"></a>Пример  
 В следующем примере создается исключение `ReferenceError` и отображается имя ошибки и ее сообщение.  
  
```JavaScript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано повторное создание ошибок и выполнение вложенных блоков `try...catch`. Если ошибка создана во вложенном блоке `try`, она передается во вложенный блок `catch`, который повторно создает ее. Вложенный блок `finally` выполняется прежде, чем внешний блок `catch` обрабатывает ошибку, и в конце выполняется внешний блок `finally`.  
  
```JavaScript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Начиная с Internet Explorer 8, стандартный режим, **перехватывать** блок больше не требуется для `finally` для запуска.  
  
## <a name="see-also"></a>См. также  
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Приложение-пример мастера настройки сценария Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)