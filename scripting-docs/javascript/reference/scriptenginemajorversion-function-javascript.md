---
title: "Функция ScriptEngineMajorVersion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion - функция"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Функция ScriptEngineMajorVersion (JavaScript)
Возвращает основной номер версии используемого обработчика скриптов.  
  
## Синтаксис  
  
```  
ScriptEngineMajorVersion()  
```  
  
## Заметки  
 Возвращаемое значение соответствует данным о версии, содержащимся в библиотеке динамической компоновки \(DLL\) для используемого языка скриптов.  
  
## Пример  
 В следующем примере показано применение функции `ScriptEngineMajorVersion`:  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Функция ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Функция ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Функция ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)