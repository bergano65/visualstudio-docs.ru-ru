---
title: "Функция ScriptEngineMajorVersion (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>Функция ScriptEngineMajorVersion (JavaScript)
Возвращает основной номер версии используемого обработчика скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращаемое значение соответствует данным о версии, содержащимся в библиотеке динамической компоновки (DLL) для используемого языка скриптов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `ScriptEngineMajorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Функция ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)