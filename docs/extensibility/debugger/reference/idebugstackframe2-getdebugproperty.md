---
title: IDebugStackFrame2::GetDebugProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c520482d78b8630c639088ca98d66782f2e2d75
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321820"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Возвращает описание свойства кадр стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Параметры
`ppDebugProp`\
[out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , описывающий свойства этого кадра стека.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызов [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) метод с соответствующими фильтрами можно получить локальные переменные, параметры метода, регистры и указатель «this», связанный с этим кадром стека.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)