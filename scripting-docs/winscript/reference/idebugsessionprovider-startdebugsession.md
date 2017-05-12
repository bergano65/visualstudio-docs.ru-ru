---
title: "IDebugSessionProvider::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProvider.StartDebugSession
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugSessionProvider::StartDebugSession"
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider::StartDebugSession
Начинает сеанс отладки с указанным приложением.  
  
## Синтаксис  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### Параметры  
 `pda`  
 \[in\] определяет приложение отладки.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Данный метод начинает сеанс отладки с указанным приложением.  Отладчик должен вызывать `IRemoteDebugApplication::ConnectDebugger` перед возвращением данного вызова.  
  
## См. также  
 [Интерфейс IDebugSessionProvider](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)