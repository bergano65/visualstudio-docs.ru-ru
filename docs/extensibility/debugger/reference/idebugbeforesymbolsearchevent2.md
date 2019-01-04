---
title: IDebugBeforeSymbolSearchEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aed9c24717866750c3b9139ab2e04b48d5eda960
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930938"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Модуль отладки (DE) отправляет этот интерфейс диспетчер отладки сеансов (SDM), чтобы задать состояние панели сообщения во время загрузки символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс, если его значение должно равно строке сообщение о состоянии во время загрузки символов. Этот интерфейс реализуется только отладчики, которые работают с или являются частью сценария интерпретаторов. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM **QueryInterface** для доступа к **IDebugEvent2** интерфейс).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE создает и отправляет этот объект события в том случае, если его значение должно равно строке сообщение о состоянии во время загрузки символов. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugBeforeSymbolSearchEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Извлекает имя модуля отлаживаемых в текущий момент.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll