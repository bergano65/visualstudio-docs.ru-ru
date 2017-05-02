---
title: "Интерфейс IDebugStackFrameSnifferEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx — интерфейс"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugStackFrameSnifferEx
Предоставляет способ отображения логических кадры стека известные компонентом.  Обработчики скриптов, как правило, реализуют данный интерфейс.  Процесс отладки использования диспетчера этот интерфейс найти все кадры стека, ассоциированные с данным потоком.  
  
> [!NOTE]
>  Этот интерфейс вызвать из потока.  Реализация интерфейса должна определить текущий поток и вернуть соответствующий перечислитель.  
  
 В дополнение к методам, наследуемым от интерфейса `IDebugStackFrameSniffer`, интерфейс `IDebugStackFrameSnifferEx` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Возвращает перечислитель кадров стека текущего потока.|