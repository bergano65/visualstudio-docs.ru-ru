---
title: IEnumDebugObjects::Reset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebeef5502787ad5ab745d72e42205d86320a8f20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914471"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Этот метод выполняет сброс перечисления к первому элементу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Параметры
 Нет

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)