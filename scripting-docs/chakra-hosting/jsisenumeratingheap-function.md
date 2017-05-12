---
title: "Функция JsIsEnumeratingHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsEnumeratingHeap"
helpviewer_keywords: 
  - "JsIsEnumeratingHeap - функция"
ms.assetid: 5d14518e-3153-43f2-9a9c-068580cbd54f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsIsEnumeratingHeap
Возвращает значение, указывающее, перечисляется ли куча текущего контекста.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsIsEnumeratingHeap(  
   _Out_ bool *isEnumeratingHeap  
);  
```  
  
#### Параметры  
 `isEnumeratingHeap`  
 Указывает, перечисляется ли куча.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается в настольных приложениях, но не поддерживается в приложениях Магазина.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)