---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
Создает новую отладка вспомогательный объект документа для данного приложения.  
  
## Синтаксис  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### Параметры  
 `punkOuter`  
 \[in\] если возвращенный объект статистической обработке, `punkOuter` указатель интерфейса на управление `IUnknown`.  В противном случае это указатель null.  
  
 `pddh`  
 \[out\] вспомогательный объект документа отладки для этого приложения.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод создает новую отладочные вспомогательный объект документа для данного приложения.  
  
## См. также  
 [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)