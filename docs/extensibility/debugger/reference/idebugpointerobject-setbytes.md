---
title: IDebugPointerObject::SetBytes Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725500"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Устанавливает значение, на что указывается из серии последовательных байтов.

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
(в) Смещение, в байтах, с самого начала объекта указал.

`dwCount`\
(в) Количество байтов для набора.

`pBytes`\
(в) Массив байтов, представляющих новое значение. Это значение хранится в объекте, начиная с данного смещения.

`pdwBytes`\
(ваут) Возвращает количество байтов на самом деле набор.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется, если указатель, представленный этим [IDebugPointerObject,](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на примитивный тип или простой массив примитивных типов (т.е. массив, который может быть представлен простой последовательностью байтов). Этот `IDebugPointerObject` объект не может быть нулевой ссылкой (он должен указывать на адрес в памяти).

## <a name="see-also"></a>См. также
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
