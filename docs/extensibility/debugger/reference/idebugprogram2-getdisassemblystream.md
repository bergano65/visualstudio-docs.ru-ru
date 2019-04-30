---
title: IDebugProgram2::GetDisassemblyStream | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcc5032fe2fa080034cda3f63a0fb013e12c42e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870398"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Получает поток Дизассемблированный код для этой программы или часть этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

#### <a name="parameters"></a>Параметры
 `dwScope`

 [in] Указывает значение из [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) перечисление, определяющее область потока Дизассемблированный код.

 `pCodeContext`

 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий положение которого следует начать поток Дизассемблированный код.

 `ppDisassemblyStream`

 [out] Возвращает [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , представляющий поток Дизассемблированный код.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_DISASM_NOTSUPPORTED` Если Дизассемблированный код не поддерживается для этой конкретной архитектуры.

## <a name="remarks"></a>Примечания
 Если `dwScopes` параметр имеет `DSS_HUGE` флаг [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) значение перечисления, то должен возвратить большое количество инструкций Дизассемблированный код, например, для всего файла дизассемблированного кода или модуля. Если `DSS_HUGE` флаг не установлен, а затем Дизассемблированный код, как ожидается, будет ограничено небольшой области, как правило, одной функции.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)