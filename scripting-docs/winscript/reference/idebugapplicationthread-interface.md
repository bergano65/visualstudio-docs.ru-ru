---
title: "Интерфейс IDebugApplicationThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread — интерфейс"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugApplicationThread
Разрешает обработчики языка и основные приложения, чтобы гарантировать синхронизацию потока и поддержки поток\- специфичные отладочных сведений о состоянии.  Этот интерфейс расширяет интерфейс `IRemoteDebugApplicationThread` для предоставления доступа, отличный от удаленного в поток.  
  
 В дополнение к методам, наследуемым от интерфейса `IRemoteDebugApplicationThread`, интерфейс `IDebugApplicationThread` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Предоставляет механизм для вызывающего кода выполняется в потоке приложения.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Определяет, является ли данный поток выполняющийся в данный момент поток.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Определяет, является ли данный поток отладчика.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Задает описание данного потока.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Задает описание состояния потока.|