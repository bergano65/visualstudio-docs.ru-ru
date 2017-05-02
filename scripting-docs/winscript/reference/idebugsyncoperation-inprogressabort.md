---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
Отменяет хода выполнения операции в другом потоке.  
  
## Синтаксис  
  
```  
HRESULT InProgressAbort();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Эта операция не может быть отменена.|  
|`E_ABORT`|Не удалось завершить операцию.|  
  
## Заметки  
 Диспетчер процесса отладки этот метод вызывается из потока отладчика для отмены операции, которая выполняется в другом потоке.  
  
 Если метод `InProgressAbort` не может выполнить операцию, он возвращает `E_ABORT` как можно скорее.  Этот метод может возвращать `E_NOTIMPL`, если операция не может быть отменена.  
  
## См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)