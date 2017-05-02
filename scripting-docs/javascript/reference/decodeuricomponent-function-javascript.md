---
title: "Функция decodeURIComponent (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent - метод"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция decodeURIComponent (JavaScript)
Получает декодированную версию закодированного компонента универсального кода ресурса \(URI\).  
  
## Синтаксис  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## Заметки  
 Обязательный аргумент `encodedURIString` — это значение, представляющее закодированный компонент URI.  
  
 URIComponent является частью целого URI.  
  
 Если строка `encodedURIString` недопустима, происходит ошибка URIError.  
  
## Пример  
 В следующем примере сначала кодируется, а затем декодируется URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)