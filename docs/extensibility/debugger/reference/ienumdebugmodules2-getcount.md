---
title: 'IEnumDebugModules2:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::GetCount
helpviewer_keywords:
- IEnumDebugModules2::GetCount
ms.assetid: f4def3d2-7cc9-4cd2-9649-3b7e00a76220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 098414d2a46e727d8e7316108bce28da53a47ffa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716556"
---
# <a name="ienumdebugmodules2getcount"></a>IEnumDebugModules2::GetCount
Возвращает количество элементов в перечислении.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount(
   ULONG* pcelt
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
 Этот метод не является частью пользовательского интерфейса перечисления com, который указывает, что `Next` `Clone` необходимо реализовать только методы,, `Skip` и `Reset` .

## <a name="see-also"></a>См. также раздел
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
