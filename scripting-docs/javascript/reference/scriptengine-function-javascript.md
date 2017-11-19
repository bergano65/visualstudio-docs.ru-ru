---
title: "Функция ScriptEngine (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengine-function-javascript"></a>Функция ScriptEngine (JavaScript)
Получает имя используемого языка скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>Примечания  
 Функция `ScriptEngine` возвращает значение JScript, показывающее, что текущим обработчиком скриптов является [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `ScriptEngine`.  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Функция ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Функция ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)