---
title: "IDebugApplicationThread::SetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetDescription"
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetDescription
Задает описание данного потока.  
  
## Синтаксис  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### Параметры  
 `pstrDescription`  
 \[in\] описание данного потока.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод задает описание данного потока.  
  
## См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)