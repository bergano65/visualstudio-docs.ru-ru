---
title: "Функция eval (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>Функция eval (JavaScript)
Результатом является [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода и выполняет его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Параметры  
 `codeString`  
 Обязательный. Объект `String` значение, содержащее допустимое [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода.  
  
## <a name="remarks"></a>Примечания  
 `eval` Функция включает динамическое выполнение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] исходный код.  
  
 `codeString` Строка анализируется с [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] средство синтаксического анализа и выполнения.  
  
 Код, переданный в `eval` функция выполняется в том же контексте, как вызов `eval` функции.  
  
 По возможности используйте [функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md) выполнить десериализацию текста JavaScript Object Notation (JSON). `JSON.parse` Функция является более безопасным и выполняется быстрее, чем `eval` функции.  
  
## <a name="example"></a>Пример  
 Следующий код инициализирует переменную `myDate` для проверки даты.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)