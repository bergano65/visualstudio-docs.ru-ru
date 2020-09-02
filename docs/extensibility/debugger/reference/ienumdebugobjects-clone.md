---
title: 'Иенумдебугобжектс:: Clone | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9784314791968a7db49c2163b94ac3bc4d0d8eb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716425"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
Этот метод возвращает копию текущего перечисления в виде отдельного объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugObjects** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Копия перечисления имеет то же состояние, что и оригинал, во время вызова этого метода. Однако исходное состояние копии и исходного состояния является отдельным и может быть изменено по отдельности.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
