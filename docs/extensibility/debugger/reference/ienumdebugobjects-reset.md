---
title: IEnumDebugОбъекты::Перезагрузка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9302330ac67cba4a9a68cacb7bc8f91aff7ad3ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716325"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Этот метод сбрасывает перечисление первого элемента.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Параметры
 Отсутствуют

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода следующий вызов [в Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
