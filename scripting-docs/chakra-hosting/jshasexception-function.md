---
title: "Функция JsHasException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException - функция"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsHasException
Определяет, находится ли среда выполнения текущего контекста в состоянии исключения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### Параметры  
 `hasException`  
 Указывает, находится ли среда выполнения текущего контекста в состоянии исключения.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Если вызов среды выполнения приводит к исключению \(в результате выполнения сценария или, например, ошибки преобразования\), среда выполнения помещается в состояние исключения. Все вызовы, адресованные любому созданному средой выполнения контексту \(кроме API исключения\), будут завершаться сбоем с состоянием ошибки `JsErrorInExceptionState` до тех пор, пока исключение не будет очищено.  
  
 Если среда выполнения текущего контекста находится в состоянии исключения, когда обратный вызов возвращается в подсистему, эта подсистема автоматически создаст исключение повторно.  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)