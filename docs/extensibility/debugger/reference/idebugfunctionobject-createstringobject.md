---
title: IDebugFunctionObject::CreateStringObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40a13b9b388caa6a1ae6e3e470e4ea02553fa0ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728514"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Создает объект строки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Параметры
`pcstrString`\
(в) Значение строки для объекта строки.

`ppObject`\
(ваут) Возвращает объект [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий вновь созданный объект строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, чтобы создать объект, представляющий строку, которая является параметром для функции, представленной интерфейсом [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
