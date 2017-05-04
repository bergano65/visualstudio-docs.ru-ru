---
title: "Интерфейс IJsDebugStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Интерфейс IJsDebugStackWalker
Представляет средство просмотра стека для указанного потока.  
  
## Синтаксис  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## Члены  
  
### Открытые методы  
  
|Имя|Описание|  
|---------|--------------|  
|[Метод IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Получает следующий кадр.|  
  
## Заметки  
 Ходоки стека можно создать, только пока целевой объект остановлен. Они становятся недействительными, как только целевой процесс продолжается.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)