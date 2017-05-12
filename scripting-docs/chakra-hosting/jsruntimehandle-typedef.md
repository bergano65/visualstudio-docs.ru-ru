---
title: "Определение типа (Typedef) JsRuntimeHandle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsRuntimeHandle
Обработчик среды выполнения Chakra.  
  
## Синтаксис  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## Заметки  
 Каждая среда выполнения Chakra имеет свой независимый механизм выполнения, JIT\-компилятор и кучу сборщика мусора.  Таким образом, каждая среда выполнения полностью изолирована от других сред.  
  
 Среды выполнения можно использовать в любом потоке, но только один поток может осуществить вызов в среду выполнения в любое время.  
  
> [!WARNING]
>  В отличие от других ссылок на объекты в хосте\-API Chakra, JsRuntimeHandle — это не собранный мусор, поскольку содержит мусор, собранный самой кучей.  Среда выполнения будет существовать, пока JsDisposeRuntime вызывается.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)