---
title: IEnumDebugModules2::Reset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b969b03c955368415d2e5911eb46731d133abad3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350324"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
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
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) метод возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)