---
title: "Метод normalize (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод normalize (String) (JavaScript)
Возвращает форму нормализации Юникода для указанной строки.  
  
## Синтаксис  
  
```  
stringObj.normalize([form]);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Строковый объект для проверки.  
  
 `form`  
 Необязательно.  Значение формы нормализации Юникода.  
  
## Возвращаемое значение  
 Форма нормализации Юникода для указанной строки.  
  
## Исключения  
 Если `form` представляет собой неподдерживаемое значение, вызывается исключение `RangeError`.  
  
## Заметки  
 Если `stringObj` не является строкой, он будет преобразован в строку до того, как метод попытается вернуть форму нормализации Юникода для строки.  
  
 `form` должно быть значением формы нормализации Юникода — NFC, NFD, NFKC или NFKD, соответствующим значениям, указанным для стандарта [Unicode Standard Annex \#15](http://www.unicode.org/reports/tr15/).  Значение по умолчанию для `form` — NFC.  
  
## Пример  
 В следующих примерах кода показано использование метода `normalize`.  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]