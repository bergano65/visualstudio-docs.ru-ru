---
title: "IDebugAsyncOperation::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Start"
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Start
Вызывает асинхронную операцию запуска.  
  
## Синтаксис  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### Параметры  
 `padocb`  
 Интерфейс обратного вызова, который получает события состояния из данной операции.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_UNEXPECTED`|Операция уже отложена.|  
  
## Заметки  
 Этот метод вызывает `IDebugSyncOperation::Execute` вызываться асинхронно в потоке, полученном из `IDebugSyncOperation::GetTargetThread`.  Этот метод следует вызывать только из потока отладчика; в противном случае он не возвратит до тех пор, пока операция не будет завершена.  
  
## См. также  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)