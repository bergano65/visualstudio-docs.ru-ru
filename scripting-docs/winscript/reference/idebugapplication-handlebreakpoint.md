---
title: 'IDebugApplication:: Хандлебреакпоинт | Документация Майкрософт'
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574964"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Заставляет текущий поток блокировать и отправлять уведомление точки останова в интегрированную среду разработки отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `br`  
 окне Причина разрыва.  
  
 `pbra`  
 заполняет Действие, выполняемое при возобновлении работы отладчика приложением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Языковой механизм вызывает этот метод в контексте потока, который достигает точки останова. Этот метод блокирует текущий поток и отправляет уведомление точки останова в интегрированную среду разработки отладчика. Когда отладчик возобновляет работу приложения, параметр `pbra` указывает, какое действие следует выполнить.  
  
> [!NOTE]
> Обработчик языка может вызываться потоком для выполнения таких задач, как перечисление кадров стека или вычисление выражений во время точки останова.  
  
 Этот метод вызывает `IApplicationDebugger::onHandleBreakPoint`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Иаппликатиондебугжер:: онхандлебреакпоинт](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)    
 @No__t_1 [перечисления бреакреасон](../../winscript/reference/breakreason-enumeration.md)  
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)