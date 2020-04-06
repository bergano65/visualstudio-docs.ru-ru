---
title: FRAMEINFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736792"
---
# <a name="frameinfo"></a>FRAMEINFO
Описывает кадр стека.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Участники
`m_dwValidFields`\
Комбинация флагов [из FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисления, которая определяет, какие поля заполнены.

`m_bstrFuncName`\
Имя функции, связанное с кадром стека.

`m_bstrReturnType`\
Тип возврата, связанный с кадром стека.

`m_bstrArgs`\
Аргументы к функции, связанной с кадром стека.

`m_bstrLanguage`\
Язык, на котором реализована функция.

`m_bstrModule`\
Имя модуля, связанное с кадром стека.

`m_addrMin`\
Минимальный физический адрес стека.

`m_addrMAX`\
Максимальный физический адрес стека.

`m_pFrame`\
Объект [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) представляющий этот кадр стека.

`m_pModule`\
Объект [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) представляющий модуль, содержащий этот кадр стека.

`m_fHasDebugInfo`\
Ненулевой`TRUE`( ), если информация об отладке существует в данном кадре.

`m_fStaleCode`\
Ненулевой`TRUE`( ), если кадр стека связан с кодом, который больше не действителен.

`m_fAnnotatedFrame`\
Ненулевой`TRUE`(), если кадр стека аннотирован менеджером отладки сеанса (SDM).

## <a name="remarks"></a>Примечания
Эта структура передается методу [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) для заполнения. Эта структура также содержится в списке, который содержится в интерфейсе [IEnumDebugFrameInfo2,](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) который, в свою очередь, возвращается из вызова в метод [EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
