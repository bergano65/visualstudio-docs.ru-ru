---
title: IEnumCodePaths2::Перезагрузка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2392c25513b53137e5cdca332bc133ab998be999
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717791"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Сбрасывает перечисление на первый элемент.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода следующий вызов [следующему](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) методу возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
