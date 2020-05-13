---
title: IDebugThread2:Резюме Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
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
(ваут) Возвращает количество приовер после операции резюме.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Каждый вызов к этому методу приостанавливает количество подставки до тех пор, пока он не достигнет 0, когда выполнение фактически возобновляется. Это количество притяжок отображается в окне отладки **потоков.**

 Для каждого вызова этого метода должен быть предыдущий вызов метода [Приостановки.](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Подсчет приостановки определяет, сколько `IDebugThread2::Suspend` раз метод был вызван до сих пор.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Приостановить](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
