---
title: FRAMEINFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84e7329acb3cdbff5c2f84fbd035867791012b2e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680507"
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
m_dwValidFields объект сочетание флагов из [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисление, указывающее, какие поля заполнены.

m_bstrFuncName имя функции, связанной с этим кадром стека.

m_bstrReturnType тип возвращаемого значения, связанные с этим кадром стека.

m_bstrArgs аргументы функции, связанные с этим кадром стека.

m_bstrLanguage язык в реализации функции.

m_bstrModule имя модуля, связанной с этим кадром стека.

m_addrMin адрес минимальное физические стеки.

m_addrMAX адрес максимальное физические стеки.

m_pFrame [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий данный кадр стека.

m_pFrame [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, содержащий данный кадр стека.

m_fHasDebugInfo ненулевое значение (`TRUE`) Если отладочная информация содержится в заданный период.

m_fHasDebugInfo ненулевое значение (`TRUE`) Если кадр стека связана с кодом, который больше не является допустимым.

m_fHasDebugInfo ненулевое значение (`TRUE`) Если кадр стека имеет аннотации диспетчер отладки сеансов (SDM).

## <a name="remarks"></a>Примечания
Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) метод для заполнения. Эта структура также содержится в списке, который содержится в [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
