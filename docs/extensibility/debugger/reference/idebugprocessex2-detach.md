---
title: IDebugProcessEx2::Detach Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723361"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Этот метод информирует процесс о том, что сеанс больше не отлажает процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Параметры
`pSession`\
(в) Значение, которое однозначно определяет сеанс, чтобы отделить этот процесс от.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Интерфейс, пройденный, `pSession` должен рассматриваться только как файлcookieое, значение, которое однозначно определяет диспетчера отладки сеанса, который первоначально прилагался к этому процессу; ни один из методов на поставляемом интерфейсе не является функциональным.

## <a name="see-also"></a>См. также
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
