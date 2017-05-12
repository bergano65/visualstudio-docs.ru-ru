---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
Ожидания для всех указанных маркеров, которые необходимо указать при крест\- включая вызовы потока, который необходимо создать в этот поток.  Этот метод должен вызываться из потока отладчика.  
  
> [!IMPORTANT]
>  [IDebugApplication110 — интерфейс](../../winscript/reference/idebugapplication110-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### Параметры  
 `handleCount`  
 Число дескрипторов ожидания.  
  
 `pHandles`  
 Набор дескрипторов ожидания.  
  
 `pIndex`  
 HRESULT со значением S\_ОК, если индекс в `pHandles` для маркера, который был подан сигнал.  
  
## См. также  
 [IDebugApplication110 — интерфейс](../../winscript/reference/idebugapplication110-interface.md)