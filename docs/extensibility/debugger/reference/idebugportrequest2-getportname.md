---
title: IDebugPortRequest2:GetPortName Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724814"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Получает название порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Параметры
`pbstrPortName`\
(ваут) Возвращает название порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Интерфейс [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) обычно передается от пакета отладки (клиента) поставщику порта (серверу) для получения подключения к порту. Как отладка пакет и поставщик порта знают о возможных вариантов для порта. Если простая строка может описать порт, то `IDebugPortRequest2::GetPortName` метод имеет достаточно информации, чтобы сделать соединение. В противном случае, дополнительные интерфейсы могут быть предоставлены `IDebugPortRequest2::QueryInterface`клиентом, которые могут быть получены на сервере с помощью.

## <a name="see-also"></a>См. также
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
