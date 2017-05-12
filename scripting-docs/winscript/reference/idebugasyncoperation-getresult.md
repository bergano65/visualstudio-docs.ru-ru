---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
Содержит возвращаемое значение и параметр объекта передачи синхронной операции из отладки.  
  
## Синтаксис  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### Параметры  
 `phrResult`  
 \[out\] если операция завершена, `phrResult` возвращаемое значение `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 \[out\] если операция завершена, `ppunkResult` параметр объекта, возвращенный операцией.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция не завершена.|  
  
## Заметки  
 Если операция завершена, возвращения этого метода `HRESULT` и параметр объекта из `IDebugSyncOperation::Execute`.  
  
## См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)