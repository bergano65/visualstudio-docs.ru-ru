---
title: 'IEnumDebugPrograms2:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68a1f33fa4512b29dc6da6927a60af382285a9ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715615"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
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

## <a name="remarks"></a>Remarks
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
