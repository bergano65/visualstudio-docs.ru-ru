---
title: "Интерфейс IRemoteDebugApplication | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication-interface"></a>Интерфейс IRemoteDebugApplication
Представляет работающее приложение. Он не соответствуют процесса операционной системы. Как правило отладчик обращается приложение для отладки. Как правило, диспетчер отладки процессов реализует объект приложения.  
  
 Помимо методов, наследуемых от `IUnknown`, `IRemoteDebugApplication` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Продолжает работу приложения, которое в данный момент точку останова.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|В результате приложения, чтобы переключиться в режим отладчика при первой возможности.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Отладчик подключается к этому приложению.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Отключает текущий отладчик из приложения.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Возвращает текущий отладчик подключается приложение.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Предоставляет механизм для отладчика интегрированной среды разработки, выполняется вне процесса для приложения, для создания объектов в процессе приложения.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Указывает, является ли скорость реагирования приложения.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Перечисляет все потоки, известно, связанных с приложением.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Возвращает имя этого узла приложения.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Возвращает узел приложения, в которой добавляются все узлы, связанные с приложением.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Перечисляет контекстов глобальные выражения для всех языков, работающих в данном приложении.|