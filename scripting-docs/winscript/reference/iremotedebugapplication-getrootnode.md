---
title: "IRemoteDebugApplication::GetRootNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetRootNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetRootNode"
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetRootNode
Возвращает узел приложения, в котором добавитьы все узлы, связанные с приложением.  
  
## Синтаксис  
  
```  
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Параметры  
 `ppdanRoot`  
 \[out\] узел приложения отладки, под которым добавитьы все узлы, связанные с приложением.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает узел приложения, в котором добавитьы все узлы, связанные с приложением.  
  
## См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)