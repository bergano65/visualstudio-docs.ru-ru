---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
Основное приложение active scripting вызывает этот метод, чтобы начать процесс сборки мусора.  
  
## Синтаксис  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### Параметры  
 `scriptgctype`  
 \[in\] [Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md), которое указывает, следует ли сделать normal или исчерпывающую сборки мусора.  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  
  
## См. также  
 [Интерфейс IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)