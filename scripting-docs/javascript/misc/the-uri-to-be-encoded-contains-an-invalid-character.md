---
title: "URI для кодирования содержит недопустимый символ | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# URI для кодирования содержит недопустимый символ
Предпринята попытка закодировать строку в виде универсального кода ресурса \(URI\), но она содержит недопустимые символы.  Хотя большинство символов можно использовать внутри строк, подлежащих преобразованию в URI, некоторые последовательности символов Юникода недопустимы.  
  
### Исправление ошибки  
  
-   Убедитесь, что кодируемая строка содержит только допустимые последовательности символов Юникода.  Полный код URI состоит из последовательности компонентов и разделителей.  Имена в угловых скобках представляют компоненты, а ":", "\/", ";" и "?" — это зарезервированные символы, используемые в качестве разделителей.  Общая форма следующая:  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)