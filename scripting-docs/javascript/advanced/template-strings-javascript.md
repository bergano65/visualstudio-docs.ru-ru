---
title: "Строки шаблона (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Строки шаблона (JavaScript)
В [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] строки шаблонов можно использовать для создания строковых литералов с внедренными выражениями.  Кроме того, строки шаблонов предоставляют встроенную поддержку многострочного текста.  
  
 Чтобы создать строку шаблона, вместо одинарных или двойных кавычек используйте гравис \(\`\), который также называют обратной кавычкой.  В следующем примере кода показана простая строка шаблона.  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 В строки шаблонов можно включать разрывы строк, не используя для этого символ перевода строки \(\\n\).  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 Символ $ позволяет ввести в строку шаблона заполнители.  В таком случае используется синтаксис ${*выражение*}, где *выражение* представляет собой любое выражение JavaScript, например переменную или функцию, как показано в следующем примере.  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 С помощью тегов можно изменять значение строки шаблона, используя для этого функцию, которую вызывают содержащиеся в такой строке аргументы.  Первый аргумент представляет собой массив строковых литералов, разделенных содержащимися в нем строковыми выражениями шаблона, а второй аргумент — массив \([параметр Rest](../../javascript/functions-javascript.md)\), содержащий значения строковых выражений шаблона.  
  
 В следующем примере используется функция шаблона с тегом buildURL, позволяющая создать URL\-адрес.  В этом случае строка шаблона вводится сразу после имени функции.  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
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
  
## См. также  
 [Справочник по языку JavaScript](../../javascript/javascript-language-reference.md)   
 [Расширенный язык JavaScript](../../javascript/advanced/advanced-javascript.md)