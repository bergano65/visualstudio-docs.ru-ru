---
title: "Функция JsCreateContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext - функция"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Функция JsCreateContext
Создает скриптовый контекст для выполнения скриптов.  
  
## Синтаксис  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### Параметры  
 `runtime`  
 Среда выполнения, в которой создается скриптовый контекст.  
  
 `debugApplication`  
 Приложение отладки, которое нужно использовать для отладки.  Этот параметр может иметь значение null, в этом случае отладка для контекста не включена.  
  
 `newContext`  
 Созданный скриптовый контекст.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Каждый скриптовый контекст имеет собственный глобальный объект, изолированный от всех остальных скриптовых контекстов.  
  
 Параметр `debugApplication` не поддерживается в режиме Edge.  Дополнительные сведения об использовании этого API в режиме Edge см. в разделе [Работа с модулем Edge и модулями предыдущих версий](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)