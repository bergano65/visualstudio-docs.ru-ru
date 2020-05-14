---
title: IDebugProcess2::EnumThreads Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724070"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Извлекает список всех потоков, работающих в процессе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugThreads2,](../../../extensibility/debugger/reference/ienumdebugthreads2.md) содержащий список всех потоков во всех программах процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод перечисляет потоки, работающие в каждой программе, а затем объединяет их в представление процесса потоков. Один поток может работать в нескольких программах; этот метод перечисляет этот поток только один раз.

 Этот метод представляет список потоков процесса без дубликатов. В противном случае, чтобы перечислить потоки, работающие в конкретной программе, используйте метод [EnumThreads.](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
