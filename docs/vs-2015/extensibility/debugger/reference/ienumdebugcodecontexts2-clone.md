---
title: IEnumDebugCodeContexts2::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Clone
helpviewer_keywords:
- IEnumDebugCodeContexts2::Clone
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46861570f5d874a0071fb3d3e67210b2b54e3fff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551783"
---
# <a name="ienumdebugcodecontexts2clone"></a>IEnumDebugCodeContexts2::Clone
Возвращает копию текущего перечисления как отдельный объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCodeContexts2 ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `ppEnum`

 [out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Копия перечисления имеет то же состояние, что исходный во время вызова этого метода. Тем не менее копии и исходного состояния отделены и могут изменяться по отдельности.

## <a name="see-also"></a>См. также
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)