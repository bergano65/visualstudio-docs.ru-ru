---
title: Оператор var (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641364"
---
# <a name="var-statement-javascript"></a>Оператор var (JavaScript)
Объявляет переменную.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Параметры  
 `variable1`  
 Имя объявляемой переменной.  
  
 `value1`  
 Начальное значение, присвоенное переменной.  
  
## <a name="remarks"></a>Примечания  
 Используйте `var` инструкции для объявления переменных. Можно назначить значения переменным, при их объявлении или более поздней версии в сценарии.  
  
 Переменная объявлена в первый раз он отображается в скрипте.  
  
 Можно объявить переменную без использования `var` ключевое слово и присвоить ей значение. Это называется *неявное объявление*, и не рекомендуется. Неявного объявления предоставляет область глобальной переменной. При объявлении переменной на уровне процедуры, вы обычно не следует раскрывать глобальной области. Следует избегать предоставления область глобальной переменной, необходимо использовать `var` ключевое слово в объявлении переменной.  
  
 Если вы не инициализировать переменную в `var` инструкции, автоматически назначается [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] значение `undefined`.  
  
## <a name="example"></a>Пример  
 Следующие примеры иллюстрируют использование `var` инструкции.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор Function](../../javascript/reference/function-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)