---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8017237af68b3dc414dc64bf6ae077387f0a600
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340383"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Получает имя порта.

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
[out] Возвращает имя порта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) обычно передается интерфейс из пакета отладки (клиент) для поставщика порта (сервер), чтобы получить соединение к порту. Размер пакета отладки и поставщика порта известно возможные варианты для порта. Если простой строки можно описать порт, а затем `IDebugPortRequest2::GetPortName` метод имеет достаточно сведений для подключения. В противном случае можно указать дополнительные интерфейсы клиентом, который можно получить с сервера с помощью `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>См. также
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)