---
title: "Функция JsEnumerateHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnumerateHeap"
helpviewer_keywords: 
  - "JsEnumerateHeap - функция"
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsEnumerateHeap
Выполняет перечисление кучи в текущем контексте.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### Параметры  
 `enumerator`  
 Перечислитель кучи.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 При перечислении кучи текущий контекст не может быть удален, и все вызовы для изменения состояния контекста будут завершаться ошибкой до тех пор, пока перечислитель кучи не будет освобожден.  
  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается в настольных приложениях, но не поддерживается в приложениях Магазина.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)