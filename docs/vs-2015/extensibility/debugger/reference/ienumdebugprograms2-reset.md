---
title: IEnumDebugPrograms2::Reset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ef5174ec476a242ec215eac5fcaf140cdec67c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562905"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
Выполняет сброс перечисления к первому элементу.

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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) метод возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)