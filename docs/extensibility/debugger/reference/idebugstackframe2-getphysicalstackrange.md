---
title: IDebugStackFrame2::GetPhysicalStackRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c325ab6cb12813000c981e978e728c251b06c55
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720904"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Получает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

#### <a name="parameters"></a>Параметры
 `paddrMin`

 [out] Возвращает наименьший физический адрес, связанный с данным кадром стека.

 `paddrMax`

 [out] Возвращает наибольший физический адрес, связанный с данным кадром стека.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Сведения, возвращаемые этим методом используется диспетчер отладки сеансов (SDM) для сортировки кадров стека.

 Предполагается, что стек вызовов растет вниз, то есть, что с более низким адресами памяти добавляются новые кадры стека. Архитектура среды выполнения необходимо указать физический стек диапазоны, которые соответствуют это предположение.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)