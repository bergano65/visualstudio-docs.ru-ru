---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
Предоставляет асинхронный доступ к заданному синхронному операции отладки.  
  
## Синтаксис  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### Параметры  
 `psdo`  
 \[in\] синхронные операции отладки объект.  
  
 `ppado`  
 \[out\] объект отладки асинхронной операции.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод позволяет обработчики языка для вычисления выражений в асинхронном режиме без явного синхронизироваться с потоком отладчика.  Дополнительные сведения см. в разделах [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) и [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)