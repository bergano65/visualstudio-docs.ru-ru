---
title: "Интерфейс IActiveScriptProfilerControl3 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Интерфейс IActiveScriptProfilerControl3
Предоставляет метод для перечисления над объектами кучи сборки мусора, связанные с обработчиком скрипта.  
  
## Синтаксис  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## Методы  
 [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Возвращает интерфейс \([Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\), который может использоваться для перебора объектов кучи сборки мусора в контексте связанного обработчика скриптов.