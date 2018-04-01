---
title: IDebugBreakEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3b58e0fb18b8f41f16a6cc92e682363ff531d5ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Этот интерфейс указывает диспетчера сеанса отладки (SDM) успешно завершена Асинхронный останов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для поддержки разрывов пользователя в программе. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовы SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) когда пользователь запросил необходимо приостановить отлаживаемой программы. Когда программа успешно приостановлен, отправляет DE `IDebugBreakEvent2` событий. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="remarks"></a>Примечания  
 Например, пользователь может выбрать **прервать все** на **отладки** меню для выхода из программы, которая выполняется в бесконечный цикл. SDM сообщает программе, чтобы остановить путем вызова [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Отправляет DE `IDebugBreakEvent2` наконец остановки программы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)