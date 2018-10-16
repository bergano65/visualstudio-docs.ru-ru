---
title: IDebugExceptionEvent2::PassToDebuggee | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8e6b53a07f191d967bbd676e6fcfc96b53dc14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113309"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Определяет исключение должны быть переданы отлаживаемой при возобновлении выполнения программы, или если исключения не следует использовать.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fPass`  
 [in] Ненулевое значение (`TRUE`), если исключение следует передавать для отлаживаемой при возобновлении выполнения программы, или нуль (`FALSE`) Если исключения не следует использовать.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызов этого метода не вызывает фактически любой код, выполняемый в отлаживаемой программы. Вызов является просто задать для состояния выполнения следующего кода. Например, вызовы [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) метод может возвращать `S_OK` с [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` набор полей `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Может появиться в Интегрированной среде разработки [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md) метод. Модуль отладки (DE) должен иметь поведение по умолчанию для обработки случаю, когда `PassToDebuggee` метод не вызывается.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)