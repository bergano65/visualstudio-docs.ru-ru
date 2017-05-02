---
title: "Синтаксические ошибки JavaScript | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ошибки [JavaScript]"
  - "синтаксические ошибки, JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Синтаксические ошибки JavaScript
Синтаксические ошибки [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] создаются, когда структура одного из операторов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] нарушает одно или несколько синтаксических правил.  
  
## Ошибки  
  
|Номер ошибки|Описание|  
|------------------|--------------|  
|1019|['break' не может находиться вне цикла](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|['continue' не может находиться вне цикла](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Условная компиляция отключена](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' в операторе switch может использоваться только один раз](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Ожидалась '\('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Ожидалась '\)'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Ожидалась '\/'](../../javascript/misc/expected-minus.md)|  
|1003|[Ожидалось ':'](../../javascript/misc/expected-colon.md)|  
|1004|[Ожидалась ';'](../../javascript/misc/expected-semicolon.md)|  
|1032|[Ожидался '@'](../../javascript/misc/expected-at.md)|  
|1029|[Ожидалось '@end'](../../javascript/misc/expected-at-end.md)|  
|1007|[Ожидалась '&#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Ожидалась '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Ожидалась '}'](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Ожидался '\='](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[Ожидалось 'catch'](../../javascript/misc/expected-catch.md)|  
|1031|[Ожидалась константа](../../javascript/misc/expected-constant.md)|  
|1023|[Ожидалась шестнадцатеричная цифра](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Ожидался идентификатор](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Ожидался идентификатор, строка или число](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Ожидалось 'while'](../../javascript/misc/expected-while.md)|  
|1014|[Недопустимый символ](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Метка не найдена](../../javascript/misc/label-not-found.md)|  
|1025|[Метка переопределена](../../javascript/misc/label-redefined.md)|  
|1018|[Оператор return за пределами функции](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Синтаксическая ошибка](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Выражение, следующее за throw, должно располагаться в той же строке кода](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Комментарий без признака завершения](../../javascript/misc/unterminated-comment.md)|  
|1015|[Строковая константа без признака завершения](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### Ошибки сервера скриптов  
 Перечисленные ниже ошибки, собственно говоря, относятся к серверу скриптов, однако пользователь иногда может с ними сталкиваться.  
  
|Ошибка|HRESULT|Описание|  
|------------|-------------|--------------|  
|SCRIPT\_E\_RECORDED|0x86664004|Записана ошибка для передачи между обработчиком скриптов и сервером.  Сервер должен передать код ошибки вызывающему объекту.|  
|SCRIPT\_E\_REPORTED|0x80020101|Обработчик скриптов сообщил серверу о необработанном исключении через интерфейс IActiveScriptSite::OnScriptError.  Сервер может проигнорировать эту ошибку.|  
|SCRIPT\_E\_PROPAGATE|0x8002010|Ошибка скрипта передается вызывающему объекту, который может выполняться в другом потоке.  Сервер должен передать код ошибки вызывающему объекту.|  
  
## См. также  
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)