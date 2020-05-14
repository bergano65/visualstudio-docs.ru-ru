---
title: IEnumDebugПрограммы2:Клон Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26a099e84414afaf84d2505b35327ed86e125292
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715726"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
Возвращает копию текущего перечисления как отдельный объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Копия перечисления имеет то же состояние, что и исходное состояние на момент вызова этого метода. Тем не менее, состояния копии и оригинала являются отдельными и могут быть изменены по отдельности.

## <a name="see-also"></a>См. также
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
