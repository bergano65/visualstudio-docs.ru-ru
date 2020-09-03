---
title: 'IDebugThread2:: Resume | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718684"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Возобновляет выполнение потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Параметры
`pdwSuspendCount`\
заполняет Возвращает счетчик приостановок после операции возобновления.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Каждый вызов этого метода уменьшает число приостановок до тех пор, пока не достигнет значения 0, после чего выполнение фактически возобновляется. Это число приостановок отображается в окне отладки **потоков** .

 Для каждого вызова этого метода должен быть предыдущий вызов метода [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Счетчик приостановов определяет, сколько раз `IDebugThread2::Suspend` был вызван метод.

## <a name="see-also"></a>См. также раздел
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Приостановить](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
