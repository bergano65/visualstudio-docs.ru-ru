---
title: Интерфейс IDebugApplicationThreadEvents110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db20440d4dc797ce9a0f21c3ac0c6c89c5d4e036
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348247"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 — интерфейс
Добавляет дополнительные события потоков. Только эти события являются локальными. То есть можно подписаться на их только в процесса отладки, с помощью [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) уведомлений и негативной рекомендации методы для объектов потока приложения PDM (объекты, реализующие [IDebugApplicationThread Интерфейс](../../winscript/reference/idebugapplicationthread-interface.md)). Они происходят в потоке, в которой они получены из.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugActivationThreadEvents110` предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Вызов в потоке, с использованием потока PDM началось переключения.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Поток возобновляет работу из точки останова и будут активными еще раз.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Поток приостанавливается для точки останова и может обрабатывать вызовы, требующие потока полностью будет приостановлено.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Вызов в потоке, с использованием потока PDM переключение завершения.|