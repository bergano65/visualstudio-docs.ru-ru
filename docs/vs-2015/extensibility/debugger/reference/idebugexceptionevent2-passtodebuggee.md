---
title: IDebugExceptionEvent2::PassToDebuggee | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991025"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет исключение должно передаваться программу, отлаживаемую при возобновлении выполнения программы, или если исключение должно быть удалено.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
