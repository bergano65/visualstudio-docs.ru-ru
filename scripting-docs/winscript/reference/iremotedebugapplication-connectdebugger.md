---
title: "IRemoteDebugApplication::ConnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ConnectDebugger
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ConnectDebugger"
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ConnectDebugger
Отладчик подключается к данному приложению.  
  
## Синтаксис  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### Параметры  
 `pad`  
 \[in\] отладчик, который требуется вложить к данному приложению.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Отладчик уже подключиться к данному приложению.|  
  
## Заметки  
 Приложение может иметь только один отладчик подключенный одновременно.  Этот метод завершается неудачей, если он уже подключения.  
  
## См. также  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)