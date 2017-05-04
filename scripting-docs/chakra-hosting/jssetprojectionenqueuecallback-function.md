---
title: "Функция JsSetProjectionEnqueueCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция JsSetProjectionEnqueueCallback
Устанавливает обратный вызов, который должен использоваться для вызова завершения проекции обратно в необходимом потоке вызывающих объектов.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### Параметры  
 `projectionEnqueueContext`  
 Обратный вызов, который будет вызываться каждый раз, когда в фоновом потоке происходит завершение проекции.  
  
 `callbackState`  
 Контекст приложения, предоставляемый в `projectionEnqueueContext`.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
 Вызов должен поступать из другого контейнера COM или из другого потока в том же MTA.  
  
 Этот API поддерживается только в режиме Edge.  
  
> [!CAUTION]
>  В настоящее время PInvoke не поддерживается для этого интерфейса API.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)