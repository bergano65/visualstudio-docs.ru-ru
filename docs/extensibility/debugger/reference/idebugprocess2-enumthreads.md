---
title: IDebugProcess2::EnumThreads | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1ca619fe00ca29fb8788a450fab1ec5237be984
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870918"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Извлекает список всех потоков, выполняемых в процессе.

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

#### <a name="parameters"></a>Параметры
 `ppEnum`

 [out] Возвращает [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) , содержащий список всех потоков во всех программах, в процессе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод перечисляет поток, выполняемый в каждой программе и затем объединяет их в представление потоков процесса. Один поток может работать в нескольких программ; Этот метод перечисляет только один раз для этого потока.

 Этот метод выводит список потоков процесса без дубликатов. В противном случае для перечисления потоков, выполняющих в конкретной программы, используйте [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) метод.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)