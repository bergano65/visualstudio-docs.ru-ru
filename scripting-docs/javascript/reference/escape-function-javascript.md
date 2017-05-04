---
title: "Функция escape (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "кодирование строковых объектов"
  - "Escape - метод"
  - "шестнадцатеричный"
  - "объект String, кодировка"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция escape (JavaScript)
Кодирует строки таким образом, чтобы они могли читаться на всех компьютерах.  Не рекомендуется.  
  
## Синтаксис  
  
```  
escape(charString)   
```  
  
## Заметки  
 Обязательный аргумент `charString` представляет собой любой объект или литерал `String` для кодирования.  
  
 Функция **escape** возвращает строковое значение \(в формате Юникода\), содержащее содержимое аргумента `charstring`.  Все пробелы, знаки пунктуации, диакритические знаки и другие знаки, не являющиеся символами ASCII, кодируются в виде `%`*xx*, где *xx* является эквивалентом шестнадцатеричного числа, представляющего данный знак.  Например, пробел возвращается в виде "%20".  
  
 Знаки, значения которых превышают 255, сохраняются в формате **%u** *xxxx*.  
  
> [!NOTE]
>  Не следует использовать функцию **escape** для кодирования универсальных кодов ресурса \(URI\).  Вместо этого используйте функции `encodeURI` и `encodeURIComponent`.  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Функция unescape](../../javascript/reference/unescape-function-javascript.md)