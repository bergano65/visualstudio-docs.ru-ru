---
title: "Функция ScriptEngineBuildVersion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion - функция"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция ScriptEngineBuildVersion (JavaScript)
Возвращает номер версии сборки используемого обработчика скриптов.  
  
## Синтаксис  
  
```  
ScriptEngineBuildVersion()  
```  
  
## Заметки  
 Возвращаемое значение соответствует данным о версии, содержащимся в библиотеке динамической компоновки \(DLL\) для используемого языка скриптов.  
  
## Пример  
 В следующем примере показано применение функции `ScriptEngineBuildVersion`.  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Функция ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Функция ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)