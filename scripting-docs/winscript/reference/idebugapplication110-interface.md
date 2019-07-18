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
ms.openlocfilehash: 0991f27077cf3ac3eb5cbfdcbb409fd5903d9a66
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446376"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 — интерфейс
`IDebugApplication110` Интерфейс расширяет функциональные возможности [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Экземпляр этого интерфейса можно получить путем вызова QueryInterface для реализации [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Выполняет синхронный вызов в основном потоке.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Делает асинхронный вызов в основном потоке.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Ожиданий для любого из указанных маркеров, который должен получить сигнал при этом межпоточные вызовы публикуемый этим потоком. Этот метод должен вызываться из потока отладчика.|