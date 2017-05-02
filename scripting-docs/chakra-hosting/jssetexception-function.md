---
title: "Функция JsSetException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException - функция"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsSetException
Переводит среду выполнения текущего контекста в состояние исключения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### Параметры  
 `exception`  
 Исключение JavaScript, которое необходимо задать для среды выполнения текущего контекста.  
  
## Возвращаемое значение  
 Значение `JsNoError`, если подсистема не переведена в состояние исключения; в противном случае — код сбоя.  
  
## Заметки  
 Если среда выполнения текущего контекста уже находится в состоянии исключения, этот API возвращает значение `JsErrorInExceptionState`.  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)