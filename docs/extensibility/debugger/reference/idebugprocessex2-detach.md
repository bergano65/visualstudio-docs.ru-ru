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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58480e52e86fc4603648d9f534cb03e944a8dde8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212889"
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

## <a name="parameters"></a>Параметры
`pSession`\
[in] Значение, уникально идентифицирующий сеанс, чтобы отключить этот процесс из.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Переданный интерфейс `pSession` является следует рассматривать только как файл cookie, значение, однозначно определяющий диспетчер отладки сеансов, которые изначально подключен к этому процессу; ни один из методов предоставленного интерфейса являются рабочими.

## <a name="see-also"></a>См. также
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)