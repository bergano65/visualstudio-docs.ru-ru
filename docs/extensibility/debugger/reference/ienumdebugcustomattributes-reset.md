---
title: 'Иенумдебугкустоматтрибутес:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 061d67e628974b001f74d81675d8dcba45968678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717214"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Сбрасывает последовательность перечисления в начало.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
