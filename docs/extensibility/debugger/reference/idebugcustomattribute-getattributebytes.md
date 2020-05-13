---
title: IDebugCustomAttribute::GetAttributeBytes Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732795"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Получает информацию о атрибутах в виде капли байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Параметры
`ppBlob`\
(в, вне) Массив, заполненный байтами атрибута.

`pdwLen`\
(в, вне) Определяет максимальное количество байтов, чтобы `ppBlob` вернуться в массив, и возвращает количество байтов, фактически написанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Установите `ppBlob` параметр на нулевое значение, чтобы вернуть количество доступных байтов атрибутов. Затем выделите массив и передайте этот массив для `ppBlob` параметра.

 Байты атрибутов представляют необработанные данные пользовательского атрибута.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
