---
title: "Функция ScriptEngineMinorVersion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion - функция"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Функция ScriptEngineMinorVersion (JavaScript)
Возвращает дополнительный номер версии используемого обработчика скриптов.  
  
## Синтаксис  
  
```  
ScriptEngineMinorVersion()  
```  
  
## Заметки  
 Возвращаемое значение соответствует данным о версии, содержащимся в библиотеке динамической компоновки \(DLL\) для используемого языка скриптов.  
  
## Пример  
 В следующем примере показано применение функции `ScriptEngineMinorVersion`.  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Функция ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)