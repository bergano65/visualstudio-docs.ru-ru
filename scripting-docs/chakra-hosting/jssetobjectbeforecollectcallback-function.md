---
title: "Функция JsSetObjectBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция JsSetObjectBeforeCollectCallback
Задает функцию обратного вызова, которая вызывается средой выполнения до сборки мусора для объекта.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### Параметры  
 `ref`  
 Объект, для которого необходимо зарегистрировать обратный вызов.  
  
 `callbackState`  
 Указываемое пользователем состояние, которое будет передано обратно в обратный вызов.  
  
 `objectBeforeCollectCallback`  
 Задаваемая функция обратного вызова.  Используйте значение NULL для очистки ранее зарегистрированного обратного вызова.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Обратный вызов выполняется в текущем потоке выполнения среды выполнения, поэтому выполнение блокируется до завершения обратного вызова.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)