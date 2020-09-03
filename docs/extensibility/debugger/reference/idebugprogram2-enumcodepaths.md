---
title: 'IDebugProgram2:: Енумкодепасс | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723030"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Возвращает список путей кода для заданной позицией в исходном файле.

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
окне Слово под курсором в представлении **источника** или **дизассемблирования** в интегрированной среде разработки.

`pStart`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий текущий контекст кода.

`pFrame`\
окне Объект [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий кадр стека, связанный с текущей точкой останова.

`fSource`\
окне Ненулевое `TRUE` значение (), если в представлении **исходного кода** или ноль ( `FALSE` ) в представлении **дизассемблирования** .

`ppEnum`\
заполняет Возвращает объект [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) , содержащий список путей кода.

`ppSafety`\
заполняет Возвращает объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий дополнительный контекст кода, который необходимо задать в качестве точки останова в случае, если выбранный путь к коду пропущен. Это может произойти в случае сокращенного логического выражения, например.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Путь кода описывает имя метода или функции, которые были вызваны для перехода к текущей точке выполнения программы. Список путей кода представляет стек вызовов.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
