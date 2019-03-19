---
title: IDebugApplication::HandleBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b05288a8863b2c555493d4a3f7ea8e2b7537d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146725"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Приводит к блокировке текущего потока и отправляет уведомление точки останова в отладчике интегрированной среды разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `br`  
 [in] Причина приостановки выполнения.  
  
 `pbra`  
 [out] Действие, выполняемое, когда отладчик возобновляет работу приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Модуль языка вызывает этот метод в контексте потока, который попадает на точку останова. Этот метод блокирует текущий поток и отправляет уведомление точки останова в отладчике интегрированной среды разработки. Когда отладчик возобновляет работу приложения, `pbra` параметр указывает, какое действие следует предпринять.  
  
> [!NOTE]
>  Модуль языка могут быть вызваны потока для выполнения задач, таких как перечисления стека кадры или вычисления выражений во время точки останова.  
  
 Этот метод вызывает `IApplicationDebugger::onHandleBreakPoint` для вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)