---
title: IDebugMemoryBytes2::ReadAt Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727530"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Читает последовательность байтов, начиная с заданного места.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Параметры
`pStartContext`\
(в) Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) определяет, где начать чтение байтов.

`dwCount`\
(в) Количество байтов для чтения. Также указывается длина массива. `rgbMemory`

`rgbMemory`\
(в, вне) Array заполнены с байтами на самом деле читать.

`pdwRead`\
(ваут) Возвращает количество смежных байтов на самом деле читать.

`pdwUnreadable`\
(в, вне) Возвращает количество нечитаемых байтов. Может быть нулевая стоимость, если клиент не заинтересован в количестве нечитаемых байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если запрашиваются 100 байтов и первые 50 читаемы, следующие 20 являются нечитаемыми, а остальные 30 читаемы, этот метод возвращается:

 *`pdwRead`No 50

 *`pdwUnreadable`No 20

 В этом случае, поскольку, `*pdwRead + *pdwUnreadable < dwCount`абонент должен сделать дополнительный вызов, чтобы прочитать оставшиеся 30 байтов из исходных 100 запрошенных и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, передаваемый в `pStartContext` параметре должны быть выдвинуты на 70.

## <a name="see-also"></a>См. также
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
