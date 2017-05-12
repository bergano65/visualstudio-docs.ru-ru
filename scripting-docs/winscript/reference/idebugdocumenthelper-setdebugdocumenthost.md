---
title: "IDebugDocumentHelper::SetDebugDocumentHost | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDebugDocumentHost
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDebugDocumentHost"
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDebugDocumentHost
Задает `IDebugDocumentHost` для этого документа.  
  
## Синтаксис  
  
```  
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### Параметры  
 `pddh`  
 \[in\] узел документа отладки.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Интерфейс `IDebugDocumentHost` используется для расцветки синтаксиса промежуточного узлов выборки отложенного текста и возвращение управления объекты для вновь созданных контекстов документа.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)