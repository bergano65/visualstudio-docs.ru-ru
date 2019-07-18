---
title: IDebugPointerObject::SetBytes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e7b3fd72285f6a6c9c4abeca4e6b262d981be8f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331554"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Задает значение, на который он указывает серию последовательных байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Параметры
`dwStart`\
[in] Указывает смещение в байтах от начала объекта.

`dwCount`\
[in] Число байтов для задания.

`pBytes`\
[in] Массив байтов, представляющий новое значение. Это значение хранится в объекте, начиная с заданного смещения.

`pdwBytes`\
[out] Возвращает число байтов, фактически задания.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется в том случае, если указатель, представленного этим объектом [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на тип-примитив или простого массива типов-примитивов (то есть массив, могут быть представлены простые последовательности байтов). Это `IDebugPointerObject` объект не может быть пустая ссылка (оно должно указывать на адрес в памяти).

## <a name="see-also"></a>См. также
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)