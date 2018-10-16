---
title: Интерфейс IDebugApplicationThread | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725954"
---
# <a name="idebugapplicationthread-interface"></a>Интерфейс IDebugApplicationThread
Позволяет модули языка и узлам для обеспечения синхронизации потоков и настройка сведений о состоянии отладки конкретного потока. Этот интерфейс расширяет интерфейс `IRemoteDebugApplicationThread` интерфейс для предоставления без удаленного доступа в поток.  
  
 Помимо методов, наследуемых от `IRemoteDebugApplicationThread`, `IDebugApplicationThread` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Предоставляет механизм для вызывающего объекта запустить код в потоке приложения.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Определяет, является ли этот поток в данный момент поток.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Определяет, является ли этот поток потока отладчика.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Задает описание для данного потока.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Задает описание состояния потока.|