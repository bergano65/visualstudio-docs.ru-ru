---
title: IDebugProgram2::EnumCodePaths Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723030"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Извлекает список путей кода для заданной позиции в исходном файле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Параметры
`pszHint`\
(в) Слово под курсором в **представлении Источника** или **разборки** в IDE.

`pStart`\
(в) Объект [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) представляющий текущий контекст кода.

`pFrame`\
(в) Объект [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) представляющий кадр стека, связанный с текущей точкой разрыва.

`fSource`\
(в) Nonzero`TRUE`( ), если в представлении **Исходного** источника, или ноль (),`FALSE`если в **представлении Разборки.**

`ppEnum`\
(ваут) Возвращает объект [IEnumCodePaths2,](../../../extensibility/debugger/reference/ienumcodepaths2.md) содержащий список путей кода.

`ppSafety`\
(ваут) Возвращает объект [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) представляющий дополнительный контекст кода, который будет установлен в качестве точки разрыва в случае пропуска выбранного пути кода. Это может произойти, например, в случае короткого замыкания булеанского выражения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Путь кода описывает имя метода или функции, которые были вызваны, чтобы добраться до текущей точки выполнения программы. Список путей кода представляет стек вызовов.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
