---
title: 'IDebugPortRequest2:: Жетпортнаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 574ea2ecb69c944bdb47ff80d7b4e26db51933da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887163"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Возвращает имя порта.

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
заполняет Возвращает имя порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Интерфейс [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) обычно передается из пакета отладки (клиента) поставщику порта (серверу) для получения подключения к порту. Как пакет отладки, так и поставщик порта знают о возможных вариантах для порта. Если в простой строке можно описать порт, то у `IDebugPortRequest2::GetPortName` метода будет достаточно сведений для установления соединения. В противном случае клиенту могут предоставляться дополнительные интерфейсы, которые могут быть получены сервером с помощью `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>См. также раздел
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
