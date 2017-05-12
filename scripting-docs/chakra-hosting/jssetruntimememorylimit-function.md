---
title: "Функция JsSetRuntimeMemoryLimit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit - функция"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsSetRuntimeMemoryLimit
Задает текущий лимит памяти для среды выполнения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### Параметры  
 `runtime`  
 Среда выполнения, лимит памяти которой необходимо задать.  
  
 `memoryLimit`  
 Новый лимит среды выполнения в байтах или \-1, если лимит памяти отсутствует.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Если лимит памяти установлен, любая операция, превышающая этот лимит, будет завершаться ошибкой с сообщением «Недостаточно памяти».  Если задано значение \-1 для лимита памяти среды выполнения, это означает, что у среды выполнения нет лимита памяти.  По умолчанию новые среды выполнения не имеют лимита памяти.  Если новый лимит памяти превышает текущее использование, вызов будет выполнен успешно, а любые дальнейшие выделения в этой среде выполнения будут завершаться ошибкой до тех пор, пока показатели использования памяти среды выполнения не опустятся ниже лимита.  
  
 Можно всегда задать лимит памяти среды выполнения независимо от того, является ли среда выполнения активной в другом потоке.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)