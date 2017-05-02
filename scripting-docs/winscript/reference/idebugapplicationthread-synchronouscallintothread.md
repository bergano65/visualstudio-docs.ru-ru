---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SynchronousCallIntoThread"
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SynchronousCallIntoThread
Предоставляет механизм для вызывающего кода выполняется в потоке приложения.  
  
## Синтаксис  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Параметры  
 `pstcb`  
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
 Этот метод предоставляет механизм для вызывающего кода выполняется в потоке отладчика.  Обработчики и узлы языка обычно используют этот метод для реализации свободен\- продетые потоками объектов на основе их отдельных реализаций продетых потоками.  
  
## См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)