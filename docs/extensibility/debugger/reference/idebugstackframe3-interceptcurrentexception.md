---
title: IDebugStackFrame3::InterceptCurrentException Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719489"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Вызывается отладчиком в текущем кадре стека, когда он хочет перехватить текущее исключение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Параметры
`dwFlags`\
(в) Определяет различные действия. В настоящее [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) время `IEA_INTERCEPT` поддерживается только INTERCEPT_EXCEPTION_ACTION значение и должно быть указано.

`pqwCookie`\
(ваут) Уникальное значение, определяющее конкретное исключение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

 Ниже приведены наиболее распространенные возвраты ошибок.

|Error|Описание|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Текущее исключение не может быть перехвачено.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Текущий кадр выполнения еще не был исследован для обработчика.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Этот метод не поддерживается для этого кадра.|

## <a name="remarks"></a>Примечания
 При броске исключения отладчик получает элемент управления от времени выполнения в ключевых точках в процессе обработки исключений. В эти ключевые моменты отладчик может задать текущую рамку стека, если кадр хочет перехватить исключение. Таким образом, перехваченное исключение по существу является обработчиком исключений на лету для кадра стека, даже если в этом кадре стека нет обработчика исключений (например, блок попытки/поймать в коде программы).

 Когда отладчик хочет знать, следует ли перехвачено исключение, он вызывает этот метод на объекте текущего кадра стека. Этот метод отвечает за обработку всех деталей исключения. Если интерфейс [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) не реализован `InterceptStackException` или метод вернет ошибку, то отладчик продолжает обработку исключения в обычном режиме.

> [!NOTE]
> Исключения могут быть перехвачены только в управляемом коде, т.е. при отладке программы, работая под временем выполнения .NET. Конечно, сторонние исполнители языка `InterceptStackException` могут внедрить в свои собственные двигатели отладки, если они того пожелают.

 После завершения перехвата сигнализируется [IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

## <a name="see-also"></a>См. также
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
