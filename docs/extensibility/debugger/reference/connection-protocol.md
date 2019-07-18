---
title: CONNECTION_PROTOCOL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f52ef7e723b583d593f6f0d4fc18f5f6909b131
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346527"
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

## <a name="fields"></a>Поля
`CONNECTION_NONE`\
Нет подключение к серверу.

`CONNECTION_UNKNOWN`\
Подключение установлено, но это неизвестного типа.

`CONNECTION_LOCAL`\
Соединение предназначено для локального сервера.

`CONNECTION_PIPE`\
Подключение осуществляется через именованный канал.

`CONNECTION_TCPIP`\
Соединение использует протокол TCP/IP.

`CONNECTION_HTTP`\
Соединение использует протокол HTTP (с помощью веб-сервера).

`CONNECTION_OTHER`\
Было установлено какое-либо иное подключения (это значение не используется в настоящее время).

## <a name="remarks"></a>Примечания
Эти значения возвращаются из [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
