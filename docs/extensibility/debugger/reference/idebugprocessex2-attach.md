---
title: IDebugProcessEx2::Прикрепите Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723379"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Этот метод информирует процесс, что сеанс теперь отлажет процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Параметры
`pSession`\
(в) Значение, которое однозначно определяет сеанс, прилагаемый к этому процессу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Интерфейс, пройденый, `pSession` должен рассматриваться только как файлcookieое, значение, которое однозначно определяет менеджер отладки сеанса, прилагающий к этому процессу; ни один из методов на поставляемом интерфейсе не является функциональным.

## <a name="see-also"></a>См. также
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
