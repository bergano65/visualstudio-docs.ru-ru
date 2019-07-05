---
title: IDebugProcess2::EnumThreads | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 664f4264fd12106fef0650a31a888470e09a3154
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353172"
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

## <a name="parameters"></a>Параметры
`ppEnum`\
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