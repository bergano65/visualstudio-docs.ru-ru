---
title: "Строки шаблона (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>Строки шаблона (JavaScript)
В [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] строки шаблонов можно использовать для создания строковых литералов с внедренными выражениями. Кроме того, строки шаблонов предоставляют встроенную поддержку многострочного текста.  
  
 Чтобы создать строку шаблона, вместо одинарных или двойных кавычек используйте гравис (`), который также называют обратной кавычкой. В следующем примере кода показана простая строка шаблона.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 В строки шаблонов можно включать разрывы строк, не используя для этого символ перевода строки (\n).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Символ $ позволяет ввести в строку шаблона заполнители. В таком случае используется синтаксис ${*выражение*}, где *выражение* представляет собой любое выражение JavaScript, например переменную или функцию, как показано в следующем примере.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 С помощью тегов можно изменять значение строки шаблона, используя для этого функцию, которую вызывают содержащиеся в такой строке аргументы. Первый аргумент представляет собой массив строковых литералов, разделенных содержащимися в нем строковыми выражениями шаблона, а второй аргумент — массив ([параметр Rest](../../javascript/functions-javascript.md)), содержащий значения строковых выражений шаблона.  
  
 В следующем примере используется функция шаблона с тегом buildURL, позволяющая создать URL-адрес. В этом случае строка шаблона вводится сразу после имени функции.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Если вам нужен доступ к необработанным значениям переданных строк, добавьте в первый аргумент, передаваемый в функцию шаблона с тегом, свойство `raw`, которое возвращает передаваемые строки в необработанном виде.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  Также для возвращения строк шаблона в необработанном виде можно использовать функцию [String.raw](../../javascript/reference/string-raw-function-javascript.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку JavaScript](../../javascript/javascript-language-reference.md)   
 [Расширенный язык JavaScript](../../javascript/advanced/advanced-javascript.md)