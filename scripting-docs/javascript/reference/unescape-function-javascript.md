---
title: "Функция unescape (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape - метод"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Функция unescape (JavaScript)
Декодирует объекты `String`, закодированные с помощью функции `escape`.  Не рекомендуется.  
  
## Синтаксис  
  
```  
unescape(charString)   
```  
  
## Заметки  
 Обязательный аргумент `charString` представляет собой объект`String` или литерал для декодирования.  
  
 Функция `unescape` возвращает строковое значение с содержимым `charstring`.  Все знаки, закодированные в виде шестнадцатеричного значения %*xx*, заменяются эквивалентами из кодировки ASCII.  
  
 Знаки, закодированные в формате **%u** *xxxx* \(знаки Юникода\), заменяются знаками Юникода в шестнадцатеричной кодировке *xxxx*.  
  
> [!NOTE]
>  Не следует использовать функцию `unescape` для декодирования универсальных кодов ресурса \(URI\).  Вместо этого используйте функции `decodeURI` и `decodeURIComponent`.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Функция escape](../../javascript/reference/escape-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)