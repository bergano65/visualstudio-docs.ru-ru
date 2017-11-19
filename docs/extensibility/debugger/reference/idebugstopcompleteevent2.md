---
title: "IDebugStopCompleteEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Модуль отладки (DE) может отправлять это необязательно событие диспетчера сеанса отладки (SDM), после остановки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Это новый интерфейс для [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Предыдущие выпуски не поддерживает асинхронной остановки.  
  
 [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в сценариях с несколькими процессами или несколькими программы. Когда одна программа отправляет событие остановки SDM, SDM запрашивает другие программы, чтобы остановить слишком.  
  
 Он используется для информирования SDM, которая перестала программы асинхронно. Это полезно для отладки обработчика интерпретатор, где иногда код не выполняется внутри отлаживаемой программы, поэтому [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может выполняться синхронно. Если модуль отладки хочет использовать асинхронные уведомления, она должна вернуть `S_ASYNC_STOP` из [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll