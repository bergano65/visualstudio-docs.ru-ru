---
title: IDebugProcessEx2::Detach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b79f1f80f9b6849c37fc9b6c4c8669f1397f0227
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538152"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Этот метод сообщает процесс, что сеанс больше не является отладка процесса.

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

#### <a name="parameters"></a>Параметры
 `pSession`

 [in] Значение, уникально идентифицирующий сеанс, чтобы отключить этот процесс из.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Переданный интерфейс `pSession` является следует рассматривать только как файл cookie, значение, однозначно определяющий диспетчер отладки сеансов, которые изначально подключен к этому процессу; ни один из методов предоставленного интерфейса являются рабочими.

## <a name="see-also"></a>См. также
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)