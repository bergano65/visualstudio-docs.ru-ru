---
title: IDebugMemoryBytes2::WriteAt Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727519"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Записывает указанное количество байтов памяти, начиная с указанного адреса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Параметры
`pStartContext`\
(в) Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) определяет, где начать писать байты.

`dwCount`\
[in] Количество записываемых байтов.

`rgbMemory`\
(в) Байты писать. Предполагается, что этот `dwCount` массив будет по крайней мере байтами по размеру.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае, возвраты, `S_FALSE` если не все `E_FAIL`байты могут быть написаны или возвращает код ошибки (обычно).

## <a name="remarks"></a>Примечания
 Если исходный адрес не находится в окне памяти, представленном этим объектом [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) нет записи и код ошибки `E_FAIL` возвращается - даже если сумма для записи перекрывается в пространстве памяти.

## <a name="see-also"></a>См. также
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
