---
title: "IDebugApplication::HandleBreakPoint | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Приводит к блокировке текущего потока и отправит уведомление точки останова в отладчике интегрированной среды разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `br`  
 [in] Причина приостановки выполнения.  
  
 `pbra`  
 [out] Действие, выполняемое при отладчик возобновляет работу приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается обработчик языка в контексте потока, который попадает на точку останова. Этот метод блокирует текущий поток и отправит уведомление точки останова в отладчике интегрированной среды разработки. Когда отладчик возобновляет работу приложения, `pbra` параметр указывает, какое действие необходимо выполнить.  
  
> [!NOTE]
>  Обработчик языка могут быть вызваны потока для выполнения задачи, такие как перечисление стека кадры и вычисления выражений во время точки останова.  
  
 Этот метод вызывает `IApplicationDebugger::onHandleBreakPoint` для вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)