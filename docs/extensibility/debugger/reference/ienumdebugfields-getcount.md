---
title: 'Иенумдебугфиелдс:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5109e3f515b98cf8d89babb7a66ec28e7849d3ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716923"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Этот метод возвращает количество элементов в перечислении.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Параметры
`pcelt`\
заполняет Возвращает количество элементов в перечислении.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод не является частью пользовательского интерфейса перечисления COM, который указывает, что необходимо реализовать только следующие методы: "только следующий", "клонировать", "пропустить" и "Сброс".

## <a name="see-also"></a>См. также раздел
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
