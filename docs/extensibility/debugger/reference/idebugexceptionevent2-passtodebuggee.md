---
title: IDebugExceptionEvent2::PassToDebuggee | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcbd37f4774f5994efb3d1b03e7153d910342f71
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990463"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Определяет исключение должно передаваться программу, отлаживаемую при возобновлении выполнения программы, или если исключение должно быть удалено.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fPass`  
 [in] Ненулевое значение (`TRUE`) Если исключение должно передаваться программу, отлаживаемую при возобновлении выполнения программы, или нуль (`FALSE`) Если исключение должно быть удалено.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызов этого метода не вызывает фактически любой код, выполняемый в отлаживаемой программы. Вызов является просто установить состояние следующего выполнения кода. Например, вызовы [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) метод может вернуть `S_OK` с [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` поле "значение" `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Интегрированная среда разработки может появиться [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md) метод. Модуль отладки (DE) должны иметь поведение по умолчанию для обработки в том случае, если `PassToDebuggee` метод не вызывается.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)