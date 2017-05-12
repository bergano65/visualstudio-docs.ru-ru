---
title: "Функция decodeURI (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI - метод"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция decodeURI (JavaScript)
Получает декодированную версию закодированного универсального кода ресурса \(URI\).  
  
## Синтаксис  
  
```  
decodeURI(URIstring)  
```  
  
## Заметки  
 Обязательный аргумент `URIstring` — это значение, представляющее закодированный универсальный код ресурса \(URI\).  
  
 Используйте функцию `decodeURI` вместо нерекомендуемой функции `unescape`.  
  
 Функция `decodeURI` возвращает строковое значение.  
  
 Если строка `URIString` недопустима, происходит ошибка URIError.  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## Пример  
 В следующем примере кода сначала кодируется компонент URI, а затем он декодируется.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Объект Global](../../javascript/reference/global-object-javascript.md)