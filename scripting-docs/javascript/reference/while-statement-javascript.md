---
title: While-оператор (JavaScript) | Документы Microsoft
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
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641254"
---
# <a name="while-statement-javascript"></a>Оператор while (JavaScript)
Выполняет инструкцию или последовательность операторов, пока заданное условие является `false`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Параметры  
 `expression`  
 Обязательный. Логическое выражение, которое проверяется перед каждой итерацией цикла. Если `expression` — `true`, цикла. Если `expression` — `false`, выполнение цикла прекращается.  
  
 `statements`  
 Необязательно. Один или несколько операторов для выполнения, если `expression` — `true`.  
  
## <a name="remarks"></a>Примечания  
 `while` Инструкции проверки `expression` до цикла. Если `expression` — `false` в настоящее время цикла не выполняется.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `while`.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор Continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)