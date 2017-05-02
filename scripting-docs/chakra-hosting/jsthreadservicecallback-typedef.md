---
title: "Определение типа (Typedef) JsThreadServiceCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsThreadServiceCallback
Обратный вызов службы потока.  
  
## Синтаксис  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### Параметры  
 обратный вызов  
 Обратный вызов для фонового рабочего элемента.  
  
 callbackData  
 Аргумент данных для передачи в обратный вызов.  
  
## Заметки  
 При вызове JsCreateRuntime узел может указать фоновую службу потока.  Если она указана, фоновые рабочие элементы передаются в узел, использующий этот обратный вызов.  Предполагается, что узел начнет выполнение фонового рабочего элемента незамедлительно и вернет значение "true" или "false", а среда выполнения будет обрабатывать рабочий элемент в потоке.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)