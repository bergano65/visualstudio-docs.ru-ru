---
title: IDebugObject::GetMemoryКонтекст (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16427685765c1471fba3993743efc204cb99c367
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726666"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Получает контекст памяти, представляющий адрес значения объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Параметры
`pContext`\
(ваут) Возвращает объект [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) представляющий адрес значения объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В контексте возвращенной памяти указывается адрес значения, представленный этим объектом [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
