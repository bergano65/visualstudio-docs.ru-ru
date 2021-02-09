---
title: 'IDebugProcessEx2:: Attach | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9b9e2fa8f636581572b97da58fb9ddefeafd375
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892545"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Этот метод информирует процесс о том, что сеанс теперь отлаживается процесс.

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
окне Значение, уникально идентифицирующее сеанс, присоединяемый к этому процессу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Переданный интерфейс `pSession` должен обрабатываться только как файл cookie, значение, однозначно идентифицирующее диспетчер отладки сеанса, присоединенный к этому процессу; ни один из методов предоставленного интерфейса не работает.

## <a name="see-also"></a>См. также раздел
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
