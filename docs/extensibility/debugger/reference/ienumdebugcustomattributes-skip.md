---
title: IEnumDebugCustomАтрибуты::Пропустить Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25086724f1fde63737275aa7995f532f119bbf82
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717147"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Пропускает определенное количество пользовательских атрибутов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip ( 
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Число пропускаемых элементов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. `S_FALSE` Возвращает, `celt` если больше, чем число оставшихся элементов; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если `celt` указывается значение, превышающее количество оставшихся элементов, перечисление устанавливается до конца и `S_FALSE` возвращается.

## <a name="see-also"></a>См. также
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
