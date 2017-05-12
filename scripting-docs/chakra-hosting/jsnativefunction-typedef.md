---
title: "Определение типа (Typedef) JsNativeFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Определение типа (Typedef) JsNativeFunction
Обратный вызов функции.  
  
## Синтаксис  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### Параметры  
 вызываемая функция  
 Объект `Function`, который представляет вызванную функцию.  
  
 isConstructCall  
 Указывает, является ли вызов регулярным или "новым".  
  
 аргументы  
 Аргументы для вызова.  
  
 argumentCount  
 Число аргументов.  
  
## Значение свойства, возвращаемое значение  
 Результат вызова \(если есть\).  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)