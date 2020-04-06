---
title: IDebugProgram2::GetDisassemblyStream Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722863"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Получает поток разборок для этой программы или части этой программы.

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

## <a name="parameters"></a>Параметры
`dwScope`\
(в) Определяет значение из [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) перечисления, определяющего область потока разборки.

`pCodeContext`\
(в) [Объект IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) представляющий положение, с чего начать поток разборки.

`ppDisassemblyStream`\
(ваут) Возвращает объект [IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) представляющий поток разборки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает, `E_DISASM_NOTSUPPORTED` если разборка не поддерживается для данной архитектуры.

## <a name="remarks"></a>Примечания
 Если `dwScopes` параметр `DSS_HUGE` имеет флаг [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) набор ежекта, то ожидается, что разборка вернет большое количество инструкций по разборке, например, для всего файла или модуля. Если `DSS_HUGE` флаг не установлен, то демонтаж, как ожидается, будет ограничен небольшой областью, как правило, одной функцией.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
