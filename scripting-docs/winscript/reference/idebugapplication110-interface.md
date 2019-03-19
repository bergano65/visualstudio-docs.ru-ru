---
title: Интерфейс IDebugApplication110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c040df103bac464e4f440f23674da966063f0ae
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149673"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 — интерфейс
`IDebugApplication110` Интерфейс расширяет функциональные возможности [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Экземпляр этого интерфейса можно получить путем вызова QueryInterface для реализации [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Выполняет синхронный вызов в основном потоке.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Делает асинхронный вызов в основном потоке.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Ожиданий для любого из указанных маркеров, который должен получить сигнал при этом межпоточные вызовы публикуемый этим потоком. Этот метод должен вызываться из потока отладчика.|