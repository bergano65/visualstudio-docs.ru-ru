---
title: IDebugThread2::Приостановка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718639"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Приостанавливает поток.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Параметры
`pdwSuspendCount`\
(ваут) Возвращает количество подтяжки после операции приостановки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Каждый вызов к этому методу приращает количество приостановки выше 0. Это количество притяжок отображается в окне отладки **потоков.**

 Для каждого вызова этого метода должен быть более поздний вызов метода [резюме.](../../../extensibility/debugger/reference/idebugthread2-resume.md)

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugthread2-resume.md)
