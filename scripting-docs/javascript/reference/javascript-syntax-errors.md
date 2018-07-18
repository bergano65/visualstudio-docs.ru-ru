---
title: Синтаксические ошибки JavaScript | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639784"
---
# <a name="javascript-syntax-errors"></a>Синтаксические ошибки JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]синтаксические ошибки возникают при структура одного из вашего [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инструкций нарушает одно или несколько синтаксических правил.  
  
## <a name="errors"></a>Ошибки  
  
|Номер ошибки|Описание|  
|------------------|-----------------|  
|1019|["break" не может находиться вне цикла](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Оператор "continue" не может быть вне цикла](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Условная компиляция отключена](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|["default" в операторе switch может использоваться только один раз](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Ожидалось "("](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Ожидалось ")"](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Ожидается «/»](../../javascript/misc/expected-minus.md)|  
|1003|[Ожидался символ ":"](../../javascript/misc/expected-colon.md)|  
|1004|[Ожидался символ ";"](../../javascript/misc/expected-semicolon.md)|  
|1032|[Ожидался символ "@"](../../javascript/misc/expected-at.md)|  
|1029|[Ожидался символ "@end"](../../javascript/misc/expected-at-end.md)|  
|1007|[Ожидалось "&#93;"](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Ожидался символ "{"](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Ожидался символ "}"](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Требуется «=»](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[Ожидалось ключевое слово "catch"](../../javascript/misc/expected-catch.md)|  
|1031|[Ожидалась константа](../../javascript/misc/expected-constant.md)|  
|1023|[Ожидалась шестнадцатеричная цифра](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Требуется идентификатор](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Ожидался идентификатор, строка или число](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Ожидалось ключевое слово "while"](../../javascript/misc/expected-while.md)|  
|1014|[Недопустимый символ](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Метка не найдена](../../javascript/misc/label-not-found.md)|  
|1025|[Метка переопределена](../../javascript/misc/label-redefined.md)|  
|1018|[Оператор return за пределами функции](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Синтаксическая ошибка](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Выражение, следующее за "throw", должно располагаться в той же строке кода](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Комментарий без признака завершения](../../javascript/misc/unterminated-comment.md)|  
|1015|[Незавершенная строковая константа](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Узел ошибок в скриптах  
 Ошибки, относящиеся к серверу скриптов правильно говорить следующие сообщения об ошибках, но может появиться их время от времени.  
  
|Ошибка|HRESULT|Описание|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Для передачи между обработчиком сценариев и узлом зарегистрировал ошибку. Узел должен передать код ошибки в вызывающем объекте.|  
|SCRIPT_E_REPORTED|0x80020101|Обработчик скриптов обнаружил необрабатываемое исключение до узла через IActiveScriptSite::OnScriptError. Эту ошибку можно игнорировать узла.|  
|SCRIPT_E_PROPAGATE|0x8002010|Ошибка сценария передается в вызывающий объект, который может находиться в другом потоке. Хост должен передать код ошибки в вызывающем объекте.|  
  
## <a name="see-also"></a>См. также  
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)