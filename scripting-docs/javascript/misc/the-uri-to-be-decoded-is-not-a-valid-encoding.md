---
title: "URI для декодирования некорректно закодирован | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# URI для декодирования некорректно закодирован
Предпринята попытка декодирования неправильно сформированного универсального кода ресурса \(URI\).  Коды URI имеют особый синтаксис; большинство символов, не являющихся буквенно\-цифровыми, должны быть закодированы, прежде чем их можно будет использовать в URI.  Для создания URI из обычной строки [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] можно использовать методы `encodeURI` и `encodeURIComponent`.  
  
 Полный код URI состоит из последовательности компонентов и разделителей.  Общая форма следующая:  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты, а ":", "\/", ";" и "?" — это зарезервированные символы, используемые в качестве разделителей.  
  
### Исправление ошибки  
  
-   Убедитесь, что декодируются только допустимые URI.  Нельзя декодировать обычные строки [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], поскольку они могут содержать недопустимые символы.  
  
## См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)