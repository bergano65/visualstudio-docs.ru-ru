---
title: "Интерфейс IDebugStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer — интерфейс"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugStackFrameSniffer
Предоставляет способ отображения логических кадры стека известные компонентом.  Обработчики скриптов, как правило, реализуют данный интерфейс.  Процесс отладки использования диспетчера этот интерфейс найти все кадры стека, ассоциированные с данным потоком.  
  
> [!NOTE]
>  Отладчик вызывает этот интерфейс из потока.  Обработчик скриптов должен определить текущий поток и вернуть соответствующий перечислитель.  
  
## Методы  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugStackFrameSniffer` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Возвращает перечислитель кадров стека текущего потока.|