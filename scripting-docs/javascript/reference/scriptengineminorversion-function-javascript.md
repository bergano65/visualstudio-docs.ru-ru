---
title: Функция ScriptEngineMinorVersion (JavaScript) | Документы Microsoft
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
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639544"
---
# <a name="scriptengineminorversion-function-javascript"></a>Функция ScriptEngineMinorVersion (JavaScript)
Возвращает дополнительный номер версии используемого обработчика скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращаемое значение соответствует данным о версии, содержащимся в библиотеке динамической компоновки (DLL) для используемого языка скриптов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `ScriptEngineMinorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Функция ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)