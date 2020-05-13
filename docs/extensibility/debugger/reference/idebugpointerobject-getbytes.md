---
title: IDebugPointerObject::GetBytes Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725513"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Получает значение, указано в виде серии последовательных байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Параметры
`dwStart`\
(в) Смещение, в байтах, с самого начала объекта указал.

`dwCount`\
(в) Количество байтов для извлечения.

`pBytes`\
(в, вне) Массив, заполняемый значением в виде серии последовательных байтов, начиная с заданного смещения от объекта, на который указывается.

`pdwBytes`\
(ваут) Возвращает количество байтов, фактически извлеченных.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется, если указатель, представленный этим [IDebugPointerObject,](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на примитивный тип или простой массив примитивных типов (т.е. массив, который может быть представлен простой последовательностью байтов).

## <a name="see-also"></a>См. также
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
