---
title: "Функция encodeURIComponent (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent - метод"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция encodeURIComponent (JavaScript)
Кодирует текстовую строку как допустимый компонент универсального кода ресурса \(URI\).  
  
## Синтаксис  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## Заметки  
 Обязательный аргумент `encodedURIString` — это значение, представляющее закодированный компонент URI.  
  
 Функция `encodeURIComponent` возвращает закодированный URI.  Если передать результат в функцию `decodeURIComponent`, будет возвращена исходная строка.  Поскольку функция `encodeURIComponent` кодирует все знаки, будьте особенно осторожны, если строка представляет путь, например \/folder1\/folder2\/default.html.  Знаки косой черты также кодируются; при передаче запроса на веб\-сервер они будут недопустимыми.  Если строка содержит несколько компонентов URI, используйте функцию `encodeURI`.  
  
## Пример  
 В следующем примере кода сначала кодируется компонент URI, а затем он декодируется.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)