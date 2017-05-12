---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
Определяет, принадлежит ли указанный документ на один из дочерних узлов данного узла.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 — интерфейс](../../winscript/reference/idebugapplicationnode100-interface.md) реализуется PDM v10.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### Параметры  
 `pSearchKey`  
 Ключ поиска.  
  
## См. также  
 [IDebugApplicationNode100 — интерфейс](../../winscript/reference/idebugapplicationnode100-interface.md)