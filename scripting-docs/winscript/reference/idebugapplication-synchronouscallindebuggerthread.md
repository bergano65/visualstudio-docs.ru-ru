---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
Предоставляет механизм для вызывающего кода выполняется в потоке отладчика.  
  
## Синтаксис  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Параметры  
 `pptc`  
 \[in\] объект вызова.  
  
 `dwParam1`  
 \[in\] первый параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 \[in\] второй параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 \[in\] третий параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Обработчики и узлы языка обычно используют этот метод для реализации свободен\- продетые потоками объектов на основе их отдельных реализаций продетых потоками.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)