---
title: "Функция JsDisableRuntimeExecution | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution - функция"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsDisableRuntimeExecution
Приостанавливает выполнение скрипта и завершает выполнение всех выполняемых скриптов в среде выполнения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Параметры  
 `runtime`  
 Приостанавливаемая среда выполнения.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Вызовы, адресованные приостановленной среде выполнения, будут завершаться сбоем до вызова метода `JsEnableRuntimeExecution`.  
  
 Этот API не обязательно вызывать в потоке, где активна среда выполнения.  Несмотря на то что среда выполнения будет приведена в приостановленное состояние, выполняемый скрипт не будет приостановлен немедленно; выполнение скрипта будет, как только возможно, завершено с неперехватываемым исключением.  
  
 Приостановка выполнения в среде выполнения, которая уже приостановлена, является холостой.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)