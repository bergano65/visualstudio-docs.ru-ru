---
title: IDebugCustomAttribute::GetAttributeBytes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551261414db9fab97f3e8c2a8fdbe518143d79c5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315186"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Возвращает сведения об атрибутах как большой двоичный объект байтов.

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
[in, out] Массив, который заполняется байты атрибута.

`pdwLen`\
[in, out] Указывает максимальное число байтов для возврата в `ppBlob` массива и возвращает количество байтов, фактически записанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Задайте `ppBlob` параметр в значение null для возврата количества атрибутов доступных байтов. Затем выделить память для массива и передать этот массив в для `ppBlob` параметра.

 Атрибут байты представляют необработанные данные настраиваемого атрибута.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)