---
title: 'IDebugMemoryBytes2:: Вритеат | Документация Майкрософт'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ff77985bca8772d92c3b90e7a727c0077137e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909902"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Записывает указанное число байтов памяти, начиная с указанного адреса.

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
окне Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , указывающий место начала записи байтов.

`dwCount`\
[in] Количество записываемых байтов.

`rgbMemory`\
окне Записываемые байты. Предполагается, что этот массив имеет размер не менее `dwCount` байт.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение, `S_FALSE` если не все байты могут быть записаны или возвращали код ошибки (обычно `E_FAIL` ).

## <a name="remarks"></a>Remarks
 Если начальный адрес не находится в окне памяти, представленном этим объектом [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , то запись не происходит и возвращается код ошибки `E_FAIL` , даже если сумма для записи пересекается с областью памяти.

## <a name="see-also"></a>См. также раздел
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
