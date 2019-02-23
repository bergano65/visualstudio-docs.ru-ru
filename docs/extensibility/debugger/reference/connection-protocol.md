---
title: CONNECTION_PROTOCOL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a7d8d056fb816a428d78a8e13455cf6ccdd8a90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705837"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Указывает протокол, используемый для обмена данными между сервером отладки и отладки пакета (DE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

#### <a name="parameters"></a>Параметры
Нет CONNECTION_NONE соединения на сервере.

CONNECTION_UNKNOWN объект соединения, но это неизвестного типа.

Соединение CONNECTION_LOCAL предназначено для локального сервера.

CONNECTION_PIPE подключение осуществляется через именованный канал.

CONNECTION_TCPIP соединение использует протокол TCP/IP.

CONNECTION_HTTP подключения используется протокол HTTP (через веб-сервер).

Было установлено какое-либо иное подключения CONNECTION_OTHER (это значение не используется в настоящее время).

## <a name="remarks"></a>Примечания
Эти значения возвращаются из [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
