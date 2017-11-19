---
title: "Интерфейс IActiveScriptProfilerControl5 | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0c8b464004337b41280d6d19821f0fb9f1f50a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5-interface"></a>Интерфейс IActiveScriptProfilerControl5
Предоставляет метод, чтобы перечислить объекты кучи GC, связанный с обработчиком скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Методы  
 [Метод IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) может использоваться для перебора объектов кучи сборщика Мусора в контексте обработчика связанных сценариев.