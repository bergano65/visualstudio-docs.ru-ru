---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
Устанавливает фильтр для указанной реализации [Интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md).  Он позволяет отладчики скрипта, чтобы отфильтровать компилятор\- приложения, созданные узлы дочернего элемента так как PDM больше не отправляет события, когда они будут создатьы или удалитьы.  По умолчанию все узлы будут отправитьо.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 — интерфейс](../../winscript/reference/idebugapplicationnode100-interface.md) реализуется PDM v10.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### Параметры  
 `dwCookie`  
 Файл cookie фильтра.  
  
 `filter`  
 Фильтр.  
  
## См. также  
 [IDebugApplicationNode100 — интерфейс](../../winscript/reference/idebugapplicationnode100-interface.md)