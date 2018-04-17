---
title: IDebugBeforeSymbolSearchEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 790aa358a40c79c7d517935192fd0155150063a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Модуль отладки (DE) отправляет этот интерфейс диспетчера сеанса отладки (SDM), чтобы задать состояние панели сообщений во время загрузки символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс, когда он должен задать панель сообщений о состоянии во время загрузки символов. Этот интерфейс реализуется только отладчики, которые работы, или являются частью интерпретаторов скрипта. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM **QueryInterface** для доступа к **IDebugEvent2** интерфейс).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда он должен задать панель сообщений о состоянии во время загрузки символов. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugBeforeSymbolSearchEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Возвращает имя модуля, в настоящее время выполняется отладка.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll