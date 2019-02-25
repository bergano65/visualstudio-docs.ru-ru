---
title: IDebugThread2::GetThreadId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85dd439729763b594076e4fab076a213c10f5a46
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702087"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Получает идентификатор потока системы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

#### <a name="parameters"></a>Параметры
`pdwThreadId`

 [out] Возвращает идентификатор потока системы.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Идентификатор потока используется для идентификации потока используется всеми потоками процесса.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объект, реализующий [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) интерфейс.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
