---
title: IDebugStackFrame2::GetPhysicalStackRange (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719667"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Получает машино-зависимое представление диапазона физических адресов, связанных с кадром стека.

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

## <a name="parameters"></a>Параметры
`paddrMin`\
(ваут) Возвращает наименьший физический адрес, связанный с этой кадром стека.

`paddrMax`\
(ваут) Возвращает наивысший физический адрес, связанный с этой кадром стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Информация, возвращенная этим методом, используется диспетчером отладки сеанса (SDM) для сортировки кадров стека.

 Предполагается, что стек вызовов растет вниз, т.е. новые кадры стека добавляются во все более низких адресах памяти. Архитектура времени выполнения должна предоставлять физические диапазоны стеков, которые соответствуют этому предположению.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
